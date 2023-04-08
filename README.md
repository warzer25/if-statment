


Join Zoom Meeting
https://us05web.zoom.us/j/4699032903?pwd=aWVwbFpxWnMrbzUrN0Nwb3ZtV0RiUT09

Meeting ID: 469 903 2903
Passcode: 450ZXL
//------------------------------------------------------------------------------------------------//

ALTER TABLE employees DROP COLUMN ID; ALTER TABLE employees ADD ID INT IDENTITY(1,1)

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
