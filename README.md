


Join Zoom Meeting
https://us05web.zoom.us/j/4699032903?pwd=aWVwbFpxWnMrbzUrN0Nwb3ZtV0RiUT09

Meeting ID: 469 903 2903
Passcode: 450ZXL









Meeting ID: 469 903 2903
Passcode: 450ZXL


        //===============================================//
        bool dataGridView1Selected = false;
    bool dataGridView2Selected = false;

    // Check if any rows are selected in the first DataGridView.
    foreach (DataGridViewRow row in dataGridView1.Rows)
    {
        if ((bool)row.Cells["CheckBoxColumn"].FormattedValue)
        {
            dataGridView1Selected = true;
            break;
        }
    }

    // Check if any rows are selected in the second DataGridView.
    foreach (DataGridViewRow row in dataGridView2.Rows)
    {
        if (row.Cells["CheckBoxColumn1"].Value != null)
        {
            dataGridView2Selected = true;
            break;
        }
    }

    // Check if rows are selected in both DataGridViews.
    if (dataGridView1Selected && dataGridView2Selected)
    {
        MessageBox.Show("Please select rows from only one DataGridView at a time.");
        return;
    }

    // If rows are selected in only one DataGridView, proceed with deleting the selected rows.
    if (dataGridView1Selected)
    {
        // Delete rows from the first DataGridView.
        // ...
    }

    if (dataGridView2Selected)
    {
        // Delete rows from the second DataGridView.
        // ...
    }
        //--------------------------------------------------//
        private void button2_Click(object sender, EventArgs e)
       {
            string pathcon = "Provider=Microsoft.ACE.OLEDB.12.0;Data Source=" + txtfilepath.Text + ";Extended Properties=Excel 12.0;";
            OleDbConnection conn = new OleDbConnection(pathcon);
            conn.Open();
            DataTable schemaTable = conn.GetOleDbSchemaTable(OleDbSchemaGuid.Tables, new object[] { null, null, null, "TABLE" });
            string sheetName = schemaTable.Rows[0]["TABLE_NAME"].ToString();
            conn.Close();
            OleDbDataAdapter da = new OleDbDataAdapter("Select * from [" + sheetName + "]", conn);
            DataTable dt = new DataTable();
            da.Fill(dt);
            dataGridView1.DataSource = dt;
       }
        private void load_data()
        {
            da = new SqlDataAdapter("select * from test_table", sqlcon);
            DataTable dt = new DataTable();
            da.Fill(dt);
            dataGridView2.DataSource = dt;
        }

        private void Form3_Load(object sender, EventArgs e)
        {
            load_data();
        }

        private void btn_save_Click(object sender, EventArgs e)
        {
            string pathcon = "Provider=Microsoft.ACE.OLEDB.12.0;Data Source=" + txtfilepath.Text + ";Extended Properties=Excel 12.0;";
            OleDbConnection conn = new OleDbConnection(pathcon);
            conn.Open();
            DataTable schemaTable = conn.GetOleDbSchemaTable(OleDbSchemaGuid.Tables, new object[] { null, null, null, "TABLE" });
            string sheetName = schemaTable.Rows[0]["TABLE_NAME"].ToString();
            conn.Close();
            OleDbDataAdapter da = new OleDbDataAdapter("Select * from [" + sheetName + "]", conn);
            DataTable dt = new DataTable();
            da.Fill(dt);

            for (int i = 0; i < Convert.ToInt32(dt.Rows.Count.ToString()); i++)
            {
                string SaceStr = "Insert into test_table (name, stage, group_type, group_ev)values(@name, @stage, @group, @grouptime)";
                SqlCommand savecmd = new SqlCommand(SaceStr, sqlcon);
                savecmd.Parameters.AddWithValue("@name", dt.Rows[i][1].ToString());
                savecmd.Parameters.AddWithValue("@stage", dt.Rows[i][2].ToString());
                savecmd.Parameters.AddWithValue("@group", dt.Rows[i][3].ToString());
                savecmd.Parameters.AddWithValue("@grouptime", dt.Rows[i][4].ToString());
                sqlcon.Open();
                savecmd.ExecuteNonQuery();
                sqlcon.Close();
            }
            load_data();
            MessageBox.Show("data is saved");
        }

//------------------------------------------------------------------------------------//

          private void insert_Click(object sender, EventArgs e)
        {
            // Find the smallest missing ID
            int smallestMissingID;
            using (con)
            {
                con.Open();
                cmd = new SqlCommand("WITH NumberSequence AS (SELECT ROW_NUMBER() OVER (ORDER BY id) AS rn FROM test_table) SELECT MIN(NumberSequence.rn) FROM NumberSequence LEFT JOIN test_table ON NumberSequence.rn = test_table.id WHERE test_table.id IS NULL", con);
                object result = cmd.ExecuteScalar();
                smallestMissingID = (result == DBNull.Value) ? GetNextAvailableID() : Convert.ToInt32(result);
                con.Close();
            }

            // Enable IDENTITY_INSERT, insert the record, and disable IDENTITY_INSERT in a single command
            using (con)
            {
                con.Open();
                cmd = new SqlCommand("SET IDENTITY_INSERT test_table ON; insert into test_table (id, name, stage, group_type, group_ev) values (@id, @name2, @stage2, @group2, @grouptime2); SET IDENTITY_INSERT test_table OFF", con);
                cmd.Parameters.AddWithValue("@id", smallestMissingID);
                cmd.Parameters.AddWithValue("@name2", txt_addname.Text);
                cmd.Parameters.AddWithValue("@stage2", txt_addstage.Text);
                cmd.Parameters.AddWithValue("@group2", txt_addgroup.Text);
                cmd.Parameters.AddWithValue("@grouptime2", txt_addgrouptime.Text);
                cmd.ExecuteNonQuery();
                con.Close();
            }

            ClearData();
        }

        private int GetNextAvailableID()
        {
            int nextID;
            using (con)
            {
                con.Open();
                cmd = new SqlCommand("SELECT MAX(id) + 1 FROM test_table", con);
                nextID = Convert.ToInt32(cmd.ExecuteScalar());
                con.Close();
            }
            return nextID;
        }
  


//------------------------------------------------------------------------------------------------//

                  private void insert_Click(object sender, EventArgs e)
                  {
                  // Find the smallest missing ID
                  cmd = new SqlCommand("WITH NumberSequence AS (SELECT ROW_NUMBER() OVER (ORDER BY id) AS rn FROM test_table) SELECT MIN(NumberSequence.rn) FROM                         NumberSequence LEFT JOIN test_table ON NumberSequence.rn = test_table.id WHERE test_table.id IS NULL", con);
                  con.Open();
                  int smallestMissingID = Convert.ToInt32(cmd.ExecuteScalar());
                  con.Close();

                  // Enable IDENTITY_INSERT, insert the record, and disable IDENTITY_INSERT in a single command
                  cmd = new SqlCommand("SET IDENTITY_INSERT test_table ON; insert into test_table (id, name, stage, group_type, group_ev) values (@id, @name2, @stage2,                   @group2, @grouptime2); SET IDENTITY_INSERT test_table OFF", con);
                  con.Open();
                  cmd.Parameters.AddWithValue("@id", smallestMissingID);
                  cmd.Parameters.AddWithValue("@name2", txt_addname.Text);
                  cmd.Parameters.AddWithValue("@stage2", txt_addstage.Text);
                  cmd.Parameters.AddWithValue("@group2", txt_addgroup.Text);
                  cmd.Parameters.AddWithValue("@grouptime2", txt_addgrouptime.Text);
                  cmd.ExecuteNonQuery();
                  con.Close();

                  ClearData();
                  }


//----------------------------------------------------------------------------------------------//

                       private void btn_delete_Click(object sender, EventArgs e)
                      {
                          // Loop through all the rows in the first DataGridView.
                          for (int i = 0; i < dataGridView1.Rows.Count; i++)
                          {
                              // Check if the row's checkbox is checked.
                              if ((bool)dataGridView1.Rows[i].Cells["CheckBoxColumn"].FormattedValue)
                              {
                                  // Get the ID of the row to be deleted.
                                  int ID = Convert.ToInt32(dataGridView1.Rows[i].Cells[2].Value);

                                  // Delete the row from the first database table.
                                  string query = "DELETE FROM test_table WHERE id = @ids";
                                  using (SqlCommand cmd = new SqlCommand(query, con))
                                  {
                                      cmd.Parameters.AddWithValue("@ids", ID);
                                      con.Open();
                                      cmd.ExecuteNonQuery();
                                      con.Close();
                                  }

                                  // Remove the row from the first DataGridView.
                                  dataGridView1.Rows.RemoveAt(i);

                                  // Decrement the counter because the number of rows in the DataGridView has changed.
                                  i--;

                                  // Update the totle_time column in the test_table.
                                  string updateQuery = "UPDATE test_table SET totle_time = totle_time - 2 WHERE id = @ids";
                                  using (SqlCommand cmd = new SqlCommand(updateQuery, con))
                                  {
                                      cmd.Parameters.AddWithValue("@ids", ID);
                                      con.Open();
                                      cmd.ExecuteNonQuery();
                                      con.Close();
                                  }
                              }
                          }

                          // Loop through all the rows in the second DataGridView.
                          for (int j = 0; j < dataGridView2.Rows.Count; j++)
                          {
                              // Check if the row's button is clicked.
                              if (dataGridView2.Rows[j].Cells["CheckBoxColumn1"].Value != null)
                              {
                                  ID2 = Convert.ToInt32(dataGridView2.Rows[j].Cells[1].Value.ToString());
                                  if (ID2 == 0)
                                  {
                                      MessageBox.Show("Please select a record to delete");
                                      return;
                                  }
                                  // Delete the row from the second database table.
                                  string query = "DELETE FROM R_table WHERE id = @ids";
                                  using (SqlCommand cmd = new SqlCommand(query, con))
                                  {
                                      cmd.Parameters.AddWithValue("@ids", ID2);
                                      con.Open();
                                      cmd.ExecuteNonQuery();
                                      con.Close();
                                  }

                                  // Remove the row from the second DataGridView.
                                  dataGridView2.Rows.RemoveAt(j);

                                  // Decrement the counter because the number of rows in the DataGridView has changed.
                                  j--;

                                  // Update the totle_time column in the R_table.
                                  string updateQuery = "UPDATE R_table SET totle_time = totle_time - 2 WHERE id = @ids";
                                  using (SqlCommand cmd = new SqlCommand(updateQuery, con))
                                  {
                                      cmd.Parameters.AddWithValue("@ids", ID2);
                                      con.Open();
                                      cmd.ExecuteNonQuery();
                                      con.Close();
                                  }
                              }
                          }
                          DisplayData2();
                          DisplayData();
                          // Show a message box to confirm that the records have been deleted successfully.
                          MessageBox.Show("Records deleted successfully!");
                      }

//---------------------------------------------------------------------------//







            //---------------------------------------------------//
            ////part-1

            //int age = 5;
            //if(age<10)
            //{
            //    Console.WriteLine("age is less than 10");
            //}

            //Console.ReadLine();

            //---------------------------------------------------//


            //Console.WriteLine("enter your age:");
            //int age = int.Parse(Console.ReadLine());
            //if (age >=18)
            //{
            //    Console.WriteLine("you are good to go");
            //}

            //Console.ReadLine();

            //---------------------------------------------------//


            //Console.WriteLine("enter your age:");
            //int age = int.Parse(Console.ReadLine());
            //if (age >= 18)
            //{
            //    if (age <= 55)
            //    {
            //        Console.WriteLine("good to go");
            //    }
            //}

            //Console.ReadLine();

            //---------------------------------------------------//
            ////part-nested

            //Console.WriteLine("enter your age:");
            //int age = int.Parse(Console.ReadLine());
            //if (age >= 18)
            //{
            //    if (age <= 55)
            //    {
            //        Console.WriteLine("good to go");
            //    }
            //}

            //Console.ReadLine();

            //---------------------------------------------------//
            ////part-2

            //int age = 5;
            //if (age < 18)
            //{
            //    Console.WriteLine("true");
            //}
            //else
            //{
            //    Console.WriteLine("false");
            //}

            //Console.ReadLine();

            //---------------------------------------------------//

            //Console.WriteLine("enter your age:");
            //int age = int.Parse(Console.ReadLine());

            //if (age >= 18)
            //{
            //    Console.WriteLine("good to go");
            //}
            //else
            //{
            //    Console.WriteLine("not 18");
            //}

            //Console.ReadLine();

            //---------------------------------------------------//
            ////part-else if

            //Console.WriteLine("enter your age:");
            //int age = int.Parse(Console.ReadLine());

            //if (age == 1)
            //{
            //    Console.WriteLine("you are 1");
            //}
            //else if (age == 2)
            //{
            //    Console.WriteLine("you are 2");
            //}
            //else if (age == 3)
            //{
            //    Console.WriteLine("you are 3");
            //}
            //else if (age == 4)
            //{
            //    Console.WriteLine("you are 4");
            //}

            //Console.ReadLine();

            //--------------------------------------------------------//
            ////part-3

            //bool x = true;
            //bool y = true;
            //bool z = x && y;

            //and
            ////T && F = T
            ////T && F = F
            ////F && F = F
            ////F && T = F

            //or
            ////T || F = T
            ////T || F = T
            ////F || T = T
            ////F || F = F



            //---------------------------------------------------//

            //Console.WriteLine("enter your age");
            //int age = int.Parse(Console.ReadLine());

            //if (age >=18 && age <=55)
            //{
            //    Console.WriteLine("good to go");
            //}
            //else
            //{
            //    Console.WriteLine("there is problem");
            //}

            //Console.ReadLine();

            //---------------------------------------------------//

            //Console.WriteLine("enter your age");
            //int age = int.Parse(Console.ReadLine());
            //Console.WriteLine("what is movie rating");
            //char rating = char.Parse(Console.ReadLine());

            //if (age <= 12 || age >= 65 && rating == 'g')
            //{
            //    Console.WriteLine("discount apply");
            //}
            // Console.ReadLine();

            //---------------------------------------------------//


            //Console.WriteLine("enter your age");
            //int age = int.Parse(Console.ReadLine());
            //Console.WriteLine("what is movie rating");
            //char rating = char.Parse(Console.ReadLine());

            //if ((age <= 12 || age >= 65) && rating == 'g')
            //{
            //    Console.WriteLine("discount apply");
            //}


            //Console.ReadLine();

            //---------------------------------------------------//
            ////part-4

            //Console.WriteLine("Enter year");
            //int year = int.Parse(Console.ReadLine());

            //if (year == 1)
            //{
            //    Console.WriteLine("Freshman");
            //}
            //else if (year == 2)
            //{
            //    Console.WriteLine("Sophomore");
            //}
            //else if (year == 3)
            //{
            //    Console.WriteLine("Junior");
            //}
            //else if (year == 4)
            //{
            //    Console.WriteLine("Senior");
            //}
            //else
            //{
            //    Console.WriteLine("Invalid year");
            //}
            //Console.ReadLine();

            //-------------------------------------------------------------//
            ////part-switch

            //Console.WriteLine("Enter year");
            //int year = int.Parse(Console.ReadLine());

            //switch (year)
            //{
            //    case 1:
            //        {
            //            Console.WriteLine("Freshman");
            //            break;
            //        }
            //    case 2:
            //        {
            //            Console.WriteLine("Sophomore");
            //            break;
            //        }
            //    case 3:
            //        {
            //            Console.WriteLine("Junior");
            //            break;
            //        }
            //    case 4:
            //        {
            //            Console.WriteLine("Senior");
            //            break;
            //        }
            //    default:
            //        {
            //            Console.WriteLine("Invalid year");
            //            break;
            //        }
            //}
            //Console.ReadLine();

            //-------------------------------------------------------------//
            ////part-5

            ////(condition) ? true : false
            //int x = 50;
            //int y = 16;

            //int biggestNumber = x > y ? x : y;
            //Console.WriteLine(biggestNumber);
            ////-------------------------------------------------------------//
            //double testScore = 95;
            //Console.WriteLine((testScore >= 60) ? "Pass" : "Fail");
            ////-------------------------------------------------------------//
            //int myInt = 5;
            //if (!(myInt >= 6))
            //{

            //}
            //Console.ReadLine();

            ////-------------------------------------------------------------//
