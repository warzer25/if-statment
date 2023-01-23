



    Copy code
    private void send_Click(object sender, EventArgs e)
    {
    if(checkBoxSelectAll.Checked) // check if the checkbox is checked
    {
        con.Open();
        foreach (DataGridViewRow row in dataGridView1.Rows)
        {
            cmd = new SqlCommand("insert into R_table (name_R, stage_R, group_R, group_ev_R,class,time,totle_time) values (@name22, @stage22, @group22, @grouptime22,@class22,@dateTime22,@totle_time)", con);
            cmd2 = new SqlCommand("update test_table set totle_time = @totle_time where id = @ID", con);
            DataGridViewCheckBoxCell cell = row.Cells[1] as DataGridViewCheckBoxCell;

            //if (cell.Value != null)
            //{
            //    if (cell.Value == cell.TrueValue)
            //    {
                    int plue = int.Parse(txt_houers.Text);

                    string id = row.Cells[2].Value.ToString().Trim();
                    string name_2 = row.Cells[3].Value.ToString().Trim();
                    string stage_3 = row.Cells[4].Value.ToString().Trim();
                    string group_4 = row.Cells[5].Value.ToString().Trim();
                    string group_time_5 = row.Cells[6].Value.ToString().Trim();
                    string totle_time = row.Cells[7].Value.ToString().Trim();

                    totle_time1 = int.Parse(totle_time);
                    //cmd.Parameters.AddWithValue("@id", id);
                    cmd.Parameters.AddWithValue("@name22", name_2);
                    cmd.Parameters.AddWithValue("@stage22", stage_3);
                    cmd.Parameters.AddWithValue("@group22", group_4);
                    cmd.Parameters.AddWithValue("@grouptime22", group_time_5);
                    cmd.Parameters.AddWithValue("@class22", box_class.Text);
                    cmd.Parameters.AddWithValue("@dateTime22", time_for_send);
                    cmd.Parameters.AddWithValue("@totle_time", totle_time1 + plue);
                    cmd2.Parameters.AddWithValue("@ID", id);
                    cmd2.Parameters.AddWithValue("@totle_time", totle_time1 + plue);
                    cmd.ExecuteNonQuery();
                    cmd2.ExecuteNonQuery();
            //    }
            //}
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
            cmd = new SqlCommand("insert into R_table (name_R, stage_R, group_R, group
            ev_R,class,time,totle_time) values (@name22, @stage22, @group22, @grouptime22,@class22,@dateTime22,@totle_time)", con);
            cmd2 = new SqlCommand("update test_table set totle_time = @totle_time where id = @ID", con);
            DataGridViewCheckBoxCell cell = row.Cells[1] as DataGridViewCheckBoxCell;

            if (cell.Value != null)
            {
                if (cell.Value == cell.TrueValue)
                {
                    int plue = int.Parse(txt_houers.Text);

                    string id = row.Cells[2].Value.ToString().Trim();
                    string name_2 = row.Cells[3].Value.ToString().Trim();
                    string stage_3 = row.Cells[4].Value.ToString().Trim();
                    string group_4 = row.Cells[5].Value.ToString().Trim();
                    string group_time_5 = row.Cells[6].Value.ToString().Trim();
                    string totle_time = row.Cells[7].Value.ToString().Trim();

                    totle_time1 = int.Parse(totle_time);
                    //cmd.Parameters.AddWithValue("@id", id);
                    cmd.Parameters.AddWithValue("@name22", name_2);
                    cmd.Parameters.AddWithValue("@stage22", stage_3);
                    cmd.Parameters.AddWithValue("@group22", group_4);
                    cmd.Parameters.AddWithValue("@grouptime22", group_time_5);
                    cmd.Parameters.AddWithValue("@class22", box_class.Text);
                    cmd.Parameters.AddWithValue("@dateTime22", time_for_send);
                    cmd.Parameters.AddWithValue("@totle_time", totle_time1 + plue);
                    cmd2.Parameters.AddWithValue("@ID", id);
                    cmd2.Parameters.AddWithValue("@totle_time", totle_time1 + plue);
                    cmd.ExecuteNonQuery();
                    cmd2.ExecuteNonQuery();
                }
            }
        }
        con.Close();
        DisplayData2();
        DisplayData();
        ClearData();
    }
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
