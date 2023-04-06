


Join Zoom Meeting
https://us05web.zoom.us/j/4699032903?pwd=aWVwbFpxWnMrbzUrN0Nwb3ZtV0RiUT09

Meeting ID: 469 903 2903
Passcode: 450ZXL
//------------------------------------------------------------------------------------------------//

            private void send_Click(object sender, EventArgs e)
        {
            int plue;
            //if (!int.TryParse(txt_houers.Text, out plue))
            //{
            //    //    MessageBox.Show("Please enter a valid integer in the textbox.");
            //    //    return;
            //}

            if (check_all.Checked) // check if the checkbox is checked
            {
                con.Open();
                foreach (DataGridViewRow row in dataGridView1.Rows)
                {
                    DataGridViewCheckBoxCell cell = row.Cells[1] as DataGridViewCheckBoxCell;
                    if (row.Cells[2].Value != null && row.Cells[2].Value.ToString() != "" &&
                        row.Cells[3].Value != null && row.Cells[3].Value.ToString() != "" &&
                        row.Cells[4].Value != null && row.Cells[4].Value.ToString() != "" &&
                        row.Cells[5].Value != null && row.Cells[5].Value.ToString() != "" &&
                        row.Cells[6].Value != null && row.Cells[6].Value.ToString() != "" )
                    {
                        plue = 2;
                        string id = row.Cells[2].Value.ToString().Trim();
                        string name_2 = row.Cells[3].Value.ToString().Trim();
                        string stage_3 = row.Cells[4].Value.ToString().Trim();

                        string group_4 = row.Cells[5].Value.ToString().Trim();
                        string group_time_5 = row.Cells[6].Value.ToString().Trim();
                        //---------------------------------------------------------------------------------//
                        cmd3 = new SqlCommand("SELECT totle_time FROM test_table WHERE id = @ID", con);
                        cmd3.Parameters.AddWithValue("@ID", id);
                        int totle_time1 = (int)cmd3.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd4 = new SqlCommand("SELECT c#_st1 FROM test_table WHERE id = @ID", con);
                        cmd4.Parameters.AddWithValue("@ID", id);
                        int c_st1 = (int)cmd4.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd5 = new SqlCommand("SELECT kurdalogy_st1 FROM test_table WHERE id = @ID", con);
                        cmd5.Parameters.AddWithValue("@ID", id);
                        int kurdalogy_st1 = (int)cmd5.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd6 = new SqlCommand("SELECT ward_st1 FROM test_table WHERE id = @ID", con);
                        cmd6.Parameters.AddWithValue("@ID", id);
                        int ward_st1 = (int)cmd6.ExecuteScalar();
                        //----------------------------------------------------------------------------------//
                        //---------------------------------------------------------------------------------//
                        cmd7 = new SqlCommand("SELECT c#_st2 FROM test_table WHERE id = @ID", con);
                        cmd7.Parameters.AddWithValue("@ID", id);
                        int c_st2 = (int)cmd7.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd8 = new SqlCommand("SELECT html_st2 FROM test_table WHERE id = @ID", con);
                        cmd8.Parameters.AddWithValue("@ID", id);
                        int html_st2 = (int)cmd8.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd9 = new SqlCommand("SELECT mobile_st2 FROM test_table WHERE id = @ID", con);
                        cmd9.Parameters.AddWithValue("@ID", id);
                        int mobile_st2 = (int)cmd9.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        SqlCommand cmd10; SqlCommand cmd11;
                        cmd10 = new SqlCommand("INSERT INTO R_table (name_R, stage_R, group_R, group_ev_R, class,                                                                               time,totle_time,c#_st1,kurdalogy_st1,ward_st1,c#_st2,html_st2,mobile_st2) " +
                        "VALUES (@name22, @stage22, @group22, @grouptime22, @class22,                                                                                                           @dateTime22,@totle_time,@c_st1,@kurdalogy_st1,@ward_st1,@c_st2,@html_st2,@mobile_st2)", con);
                        //---------------------------------------------------------------------------------//
                        cmd10.Parameters.AddWithValue("@ID", id);
                        cmd10.Parameters.AddWithValue("@name22", name_2);
                        cmd10.Parameters.AddWithValue("@stage22", stage_3);
                        cmd10.Parameters.AddWithValue("@group22", group_4);
                        cmd10.Parameters.AddWithValue("@grouptime22", group_time_5);
                        cmd10.Parameters.AddWithValue("@class22", box_class.Text);
                        cmd10.Parameters.AddWithValue("@dateTime22", time_for_send);
                        //---------------------------------------------------------------------------------//
                        if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "c#")
                        {
                            if (Box_stage.SelectedItem.ToString() == "1")
                            {
                                //-----------------------------------------------------------------------------------------------------------//
                                cmd11 = new SqlCommand("UPDATE test_table SET c#_st1 = @c_st1, totle_time = @totle_time  WHERE id = @ID", con);
                                //-----------------------------------------------------------------------------------------------------------//
                                c_st1 += plue; totle_time1 += plue;
                                //--------------------------------------------------------------//
                                cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                                cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                                cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                                cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                                cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                                cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                                cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                                cmd11.Parameters.AddWithValue("@ID", id);
                                cmd11.Parameters.AddWithValue("@c_st1", c_st1);
                                cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                                //-----------------------------------------------------------//
                                cmd10.ExecuteNonQuery();
                                cmd11.ExecuteNonQuery();
                                //----------------------------//
                            }
                            else if (Box_stage.SelectedItem.ToString() == "2")
                            {

                                //-----------------------------------------------------------------------------------------------------------//
                                cmd11 = new SqlCommand("UPDATE test_table SET c#_st2 = @c_st2, totle_time = @totle_time  WHERE id = @ID", con);
                                //-----------------------------------------------------------------------------------------------------------//
                                c_st2 += plue; totle_time1 += plue;
                                //--------------------------------------------------------------//
                                cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                                cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                                cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                                cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                                cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                                cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                                cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                                cmd11.Parameters.AddWithValue("@ID", id);
                                cmd11.Parameters.AddWithValue("@c_st2", c_st2);
                                cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                                //-----------------------------------------------------------//
                                cmd10.ExecuteNonQuery();
                                cmd11.ExecuteNonQuery();
                                //----------------------------//

                            }
                        }
                        else if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "kurdalogy")
                        {
                            //-----------------------------------------------------------------------------------------------------------//
                            cmd11 = new SqlCommand("UPDATE test_table SET kurdalogy_st1 = @kurdalogy_st1, totle_time = @totle_time  WHERE id = @ID", con);
                            //-----------------------------------------------------------------------------------------------------------//
                            kurdalogy_st1 += plue; totle_time1 += plue;
                            //--------------------------------------------------------------//
                            cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                            cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                            cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                            cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                            cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                            cmd11.Parameters.AddWithValue("@ID", id);
                            cmd11.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                            //-----------------------------------------------------------//
                            cmd10.ExecuteNonQuery();
                            cmd11.ExecuteNonQuery();
                            //----------------------------//
                        }
                        else if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "ward")
                        {
                            //------------------------------------------------------------------------------------------------------------------//
                            cmd11 = new SqlCommand("UPDATE test_table SET ward_st1 = @ward_st1, totle_time = @totle_time  WHERE id = @ID", con);
                            //------------------------------------------------------------------------------------------------------------------//
                            ward_st1 += plue; totle_time1 += plue;
                            //--------------------------------------------------------------//
                            cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                            cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                            cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                            cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                            cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                            cmd11.Parameters.AddWithValue("@ID", id);
                            cmd11.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                            //-----------------------------------------------------------//
                            cmd10.ExecuteNonQuery();
                            cmd11.ExecuteNonQuery();
                            //-----------------------//
                        }
                        else if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "html")
                        {
                            //------------------------------------------------------------------------------------------------------------------//
                            cmd11 = new SqlCommand("UPDATE test_table SET html_st2 = @html_st2, totle_time = @totle_time  WHERE id = @ID", con);
                            //------------------------------------------------------------------------------------------------------------------//
                            html_st2 += plue; totle_time1 += plue;
                            //--------------------------------------------------------------//
                            cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                            cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                            cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                            cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                            cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                            cmd11.Parameters.AddWithValue("@ID", id);
                            cmd11.Parameters.AddWithValue("@html_st2", ward_st1);
                            cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                            //-----------------------------------------------------------//
                            cmd10.ExecuteNonQuery();
                            cmd11.ExecuteNonQuery();
                            //-----------------------//
                        }
                        else if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "mobile")
                        {
                            //------------------------------------------------------------------------------------------------------------------//
                            cmd11 = new SqlCommand("UPDATE test_table SET mobile_st2 = @mobile_st2, totle_time = @totle_time  WHERE id = @ID", con);
                            //------------------------------------------------------------------------------------------------------------------//
                            mobile_st2 += plue; totle_time1 += plue;
                            //--------------------------------------------------------------//
                            cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                            cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                            cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                            cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                            cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                            cmd11.Parameters.AddWithValue("@ID", id);
                            cmd11.Parameters.AddWithValue("@mobile_st2", ward_st1);
                            cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                            //-----------------------------------------------------------//
                            cmd10.ExecuteNonQuery();
                            cmd11.ExecuteNonQuery();
                            //-----------------------//
                        }

                    }


                }
                con.Close();
                DisplayData2();
                DisplayData();
                ClearData();
            }
            else
            {

                con.Open();
                foreach (DataGridViewRow row in dataGridView1.Rows)
                {
                    DataGridViewCheckBoxCell cell = row.Cells[1] as DataGridViewCheckBoxCell;
                    if (cell.Value != null && cell.Value == cell.TrueValue)
                    {
                        plue = 2;
                        string id = row.Cells[2].Value.ToString().Trim();
                        string name_2 = row.Cells[3].Value.ToString().Trim();
                        string stage_3 = row.Cells[4].Value.ToString().Trim();

                        string group_4 = row.Cells[5].Value.ToString().Trim();
                        string group_time_5 = row.Cells[6].Value.ToString().Trim();
                        //---------------------------------------------------------------------------------//
                        cmd3 = new SqlCommand("SELECT totle_time FROM test_table WHERE id = @ID", con);
                        cmd3.Parameters.AddWithValue("@ID", id);
                        int totle_time1 = (int)cmd3.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd4 = new SqlCommand("SELECT c#_st1 FROM test_table WHERE id = @ID", con);
                        cmd4.Parameters.AddWithValue("@ID", id);
                        int c_st1 = (int)cmd4.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd5 = new SqlCommand("SELECT kurdalogy_st1 FROM test_table WHERE id = @ID", con);
                        cmd5.Parameters.AddWithValue("@ID", id);
                        int kurdalogy_st1 = (int)cmd5.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd6 = new SqlCommand("SELECT ward_st1 FROM test_table WHERE id = @ID", con);
                        cmd6.Parameters.AddWithValue("@ID", id);
                        int ward_st1 = (int)cmd6.ExecuteScalar();
                        //----------------------------------------------------------------------------------//
                        //---------------------------------------------------------------------------------//
                        cmd7 = new SqlCommand("SELECT c#_st2 FROM test_table WHERE id = @ID", con);
                        cmd7.Parameters.AddWithValue("@ID", id);
                        int c_st2 = (int)cmd7.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd8 = new SqlCommand("SELECT html_st2 FROM test_table WHERE id = @ID", con);
                        cmd8.Parameters.AddWithValue("@ID", id);
                        int html_st2 = (int)cmd8.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        cmd9 = new SqlCommand("SELECT mobile_st2 FROM test_table WHERE id = @ID", con);
                        cmd9.Parameters.AddWithValue("@ID", id);
                        int mobile_st2 = (int)cmd9.ExecuteScalar();
                        //---------------------------------------------------------------------------------//
                        SqlCommand cmd10; SqlCommand cmd11;
                        cmd10 = new SqlCommand("INSERT INTO R_table (name_R, stage_R, group_R, group_ev_R, class,                                                                               time,totle_time,c#_st1,kurdalogy_st1,ward_st1,c#_st2,html_st2,mobile_st2) " +
                        "VALUES (@name22, @stage22, @group22, @grouptime22, @class22,                                                                                                           @dateTime22,@totle_time,@c_st1,@kurdalogy_st1,@ward_st1,@c_st2,@html_st2,@mobile_st2)", con);
                        //---------------------------------------------------------------------------------//
                        cmd10.Parameters.AddWithValue("@ID", id);
                        cmd10.Parameters.AddWithValue("@name22", name_2);
                        cmd10.Parameters.AddWithValue("@stage22", stage_3);
                        cmd10.Parameters.AddWithValue("@group22", group_4);
                        cmd10.Parameters.AddWithValue("@grouptime22", group_time_5);
                        cmd10.Parameters.AddWithValue("@class22", box_class.Text);
                        cmd10.Parameters.AddWithValue("@dateTime22", time_for_send);
                        //---------------------------------------------------------------------------------//
                        if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "c#")
                        {
                            if (Box_stage.SelectedItem.ToString() == "1")
                            {
                                //-----------------------------------------------------------------------------------------------------------//
                                cmd11 = new SqlCommand("UPDATE test_table SET c#_st1 = @c_st1, totle_time = @totle_time  WHERE id = @ID", con);
                                //-----------------------------------------------------------------------------------------------------------//
                                c_st1 += plue; totle_time1 += plue;
                                //--------------------------------------------------------------//
                                cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                                cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                                cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                                cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                                cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                                cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                                cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                                cmd11.Parameters.AddWithValue("@ID", id);
                                cmd11.Parameters.AddWithValue("@c_st1", c_st1);
                                cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                                //-----------------------------------------------------------//
                                cmd10.ExecuteNonQuery();
                                cmd11.ExecuteNonQuery();
                                //----------------------------//
                            }
                            else if (Box_stage.SelectedItem.ToString() == "2")
                            {

                                //-----------------------------------------------------------------------------------------------------------//
                                cmd11 = new SqlCommand("UPDATE test_table SET c#_st2 = @c_st2, totle_time = @totle_time  WHERE id = @ID", con);
                                //-----------------------------------------------------------------------------------------------------------//
                                c_st2 += plue; totle_time1 += plue;
                                //--------------------------------------------------------------//
                                cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                                cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                                cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                                cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                                cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                                cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                                cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                                cmd11.Parameters.AddWithValue("@ID", id);
                                cmd11.Parameters.AddWithValue("@c_st2", c_st2);
                                cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                                //-----------------------------------------------------------//
                                cmd10.ExecuteNonQuery();
                                cmd11.ExecuteNonQuery();
                                //----------------------------//

                            }
                        }
                        else if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "kurdalogy")
                        {
                            //-----------------------------------------------------------------------------------------------------------//
                            cmd11 = new SqlCommand("UPDATE test_table SET kurdalogy_st1 = @kurdalogy_st1, totle_time = @totle_time  WHERE id = @ID", con);
                            //-----------------------------------------------------------------------------------------------------------//
                            kurdalogy_st1 += plue; totle_time1 += plue;
                            //--------------------------------------------------------------//
                            cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                            cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                            cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                            cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                            cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                            cmd11.Parameters.AddWithValue("@ID", id);
                            cmd11.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                            //-----------------------------------------------------------//
                            cmd10.ExecuteNonQuery();
                            cmd11.ExecuteNonQuery();
                            //----------------------------//
                        }
                        else if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "ward")
                        {
                            //------------------------------------------------------------------------------------------------------------------//
                            cmd11 = new SqlCommand("UPDATE test_table SET ward_st1 = @ward_st1, totle_time = @totle_time  WHERE id = @ID", con);
                            //------------------------------------------------------------------------------------------------------------------//
                            ward_st1 += plue; totle_time1 += plue;
                            //--------------------------------------------------------------//
                            cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                            cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                            cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                            cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                            cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                            cmd11.Parameters.AddWithValue("@ID", id);
                            cmd11.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                            //-----------------------------------------------------------//
                            cmd10.ExecuteNonQuery();
                            cmd11.ExecuteNonQuery();
                            //-----------------------//
                        }
                        else if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "html")
                        {
                            //------------------------------------------------------------------------------------------------------------------//
                            cmd11 = new SqlCommand("UPDATE test_table SET html_st2 = @html_st2, totle_time = @totle_time  WHERE id = @ID", con);
                            //------------------------------------------------------------------------------------------------------------------//
                            html_st2 += plue; totle_time1 += plue;
                            //--------------------------------------------------------------//
                            cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                            cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                            cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                            cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                            cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                            cmd11.Parameters.AddWithValue("@ID", id);
                            cmd11.Parameters.AddWithValue("@html_st2", ward_st1);
                            cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                            //-----------------------------------------------------------//
                            cmd10.ExecuteNonQuery();
                            cmd11.ExecuteNonQuery();
                            //-----------------------//
                        }
                        else if (box_class.SelectedItem != null && box_class.SelectedItem.ToString() == "mobile")
                        {
                            //------------------------------------------------------------------------------------------------------------------//
                            cmd11 = new SqlCommand("UPDATE test_table SET mobile_st2 = @mobile_st2, totle_time = @totle_time  WHERE id = @ID", con);
                            //------------------------------------------------------------------------------------------------------------------//
                            mobile_st2 += plue; totle_time1 += plue;
                            //--------------------------------------------------------------//
                            cmd10.Parameters.AddWithValue("@totle_time", totle_time1);
                            cmd10.Parameters.AddWithValue("@c_st1", c_st1);
                            cmd10.Parameters.AddWithValue("@kurdalogy_st1", kurdalogy_st1);
                            cmd10.Parameters.AddWithValue("@ward_st1", ward_st1);
                            cmd10.Parameters.AddWithValue("@c_st2", c_st2);
                            cmd10.Parameters.AddWithValue("@html_st2", html_st2);
                            cmd10.Parameters.AddWithValue("@mobile_st2", mobile_st2);

                            cmd11.Parameters.AddWithValue("@ID", id);
                            cmd11.Parameters.AddWithValue("@mobile_st2", ward_st1);
                            cmd11.Parameters.AddWithValue("@totle_time", totle_time1);
                            //-----------------------------------------------------------//
                            cmd10.ExecuteNonQuery();
                            cmd11.ExecuteNonQuery();
                            //-----------------------//
                        }
                    }
                }

                con.Close();
                DisplayData2();
                DisplayData();
                ClearData();



            }
        }


//----------------------------------------------------------------------------------------------//

            if (string.IsNullOrEmpty(box_class.Text) || !int.TryParse(txt_houers.Text, out int increst_time))
            {
            MessageBox.Show("Please enter valid inputs in the textboxes.");
            return;
            }
            
//------------------------------------------------------------------------------------------//

    private void search_Click(object sender, EventArgs e)
        {
            DisplayData();
            DisplayData2();
            if (string.IsNullOrEmpty(Box_stage.Text) && string.IsNullOrEmpty(Box_group.Text) && string.IsNullOrEmpty(Box_group_time.Text))
            {
                MessageBox.Show("Please fill at least one field before clicking search.");
                return;
            }

            //butn-search-1
            string stage = Box_stage.Text;
            string group = Box_group.Text;
            string groupTime = Box_group_time.Text;

            string query = "SELECT id,name,stage,group_type,group_ev FROM test_table WHERE 1 = 1";

            if (!string.IsNullOrEmpty(stage))
            {
                query += " AND stage LIKE '%' + @stage + '%'";
            }
            if (!string.IsNullOrEmpty(group))
            {
                query += " AND group_type LIKE '%' + @group + '%'";
            }
            if (!string.IsNullOrEmpty(groupTime))
            {
                query += " AND group_ev LIKE '%' + @groupTime + '%'";
            }

            using (SqlCommand cmd = new SqlCommand(query, con))
            {
                if (!string.IsNullOrEmpty(stage))
                {
                    cmd.Parameters.AddWithValue("@stage", stage);
                }
                if (!string.IsNullOrEmpty(group))
                {
                    cmd.Parameters.AddWithValue("@group", group);
                }
                if (!string.IsNullOrEmpty(groupTime))
                {
                    cmd.Parameters.AddWithValue("@groupTime", groupTime);
                }

                con.Open();
                SqlDataAdapter da = new SqlDataAdapter(cmd);
                DataTable dt = new DataTable();
                da.Fill(dt);
                dataGridView1.DataSource = dt;
                con.Close();
            }

            ClearData();
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
