 Join Zoom Meeting
https://us05web.zoom.us/j/4699032903?pwd=aWVwbFpxWnMrbzUrN0Nwb3ZtV0RiUT09

Meeting ID: 469 903 2903
Passcode: 450ZXL










    Copy code
    pprivate void dataGridView1_CellValueChanged(object sender, DataGridViewCellEventArgs e)
    {
    if (e.RowIndex >= 0 && e.RowIndex < dataGridView1.Rows.Count)
    {
        ID = Convert.ToInt32(dataGridView1.Rows[e.RowIndex].Cells[2].Value.ToString());
        name_t = dataGridView1.Rows[e.RowIndex].Cells[3].Value.ToString();
        Box_stage.Text = dataGridView1.Rows[e.RowIndex].Cells[4].Value.ToString();
        Box_group.Text = dataGridView1.Rows[e.RowIndex].Cells[5].Value.ToString();
        Box_group_time.Text = dataGridView1.Rows[e.RowIndex].Cells[6].Value.ToString();
        totle_time2 = Convert.ToInt32(dataGridView1.Rows[e.RowIndex].Cells[7].Value.ToString());
        cmd = new SqlCommand("update test_table set name=@name3,stage=@stage3, group_type=@group3, group_ev=@group_time3,totle_time = @totle_time where ID=@id", con);
        con.Open();
        cmd.Parameters.AddWithValue("@name3", name_t);
        cmd.Parameters.AddWithValue("@id", ID);
        cmd.Parameters.AddWithValue("@stage3", Box_stage.Text);
        cmd.Parameters.AddWithValue("@group3", Box_group.Text);
        cmd.Parameters.AddWithValue("@group_time3", Box_group_time.Text);
        cmd.Parameters.AddWithValue("@totle_time", totle_time2);
        cmd.ExecuteNonQuery();

        con.Close();
        ClearData();
    }
    }
    private void dataGridView2_CellValueChanged(object sender, DataGridViewCellEventArgs e)
    {
    if (e.RowIndex >= 0 && dataGridView2.Rows.Count > 0)
    {
        int rowIndex = e.RowIndex;
        if (dataGridView2.Rows[rowIndex].Cells[1].Value != null)
        {
            ID2 = Convert.ToInt32(dataGridView2.Rows[rowIndex].Cells[1].Value.ToString());
        }
        if (dataGridView2.Rows[rowIndex].Cells[2].Value != null)
        {
            name_t2 = dataGridView2.Rows[rowIndex].Cells[2].Value.ToString();
        }
        if (dataGridView2.Rows[rowIndex].Cells[3].Value != null)
        {
            Box_stage.Text = dataGridView2.Rows[rowIndex].Cells[3].Value.ToString();
        }
        if (dataGridView2.Rows[rowIndex].Cells[4].Value != null)
        {
            Box_group.Text = dataGridView2.Rows[rowIndex].Cells[4].Value.ToString();
        }
        if (dataGridView2.Rows[rowIndex].Cells[5].Value != null)
        {
            Box_group_time.Text = dataGridView2.Rows[rowIndex].Cells[5].Value.ToString();
        }
        if (dataGridView2.Rows[rowIndex].Cells[6].Value != null)
        {
            box_class.Text = dataGridView2.Rows[rowIndex].Cells[6].Value.ToString();
        }
        if (dataGridView2.Rows[rowIndex].Cells[7].Value != null)
        {
            txt_time.Text = dataGridView2.Rows[rowIndex].Cells[7].Value.ToString();
        }
        if (dataGridView2.Rows[rowIndex].Cells[8].Value != null)
        {
            totle_time3 = Convert.ToInt32(dataGridView2.Rows[rowIndex].Cells[8].Value.ToString());
        }


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
