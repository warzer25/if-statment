Join Zoom Meeting
https://us05web.zoom.us/j/4699032903?pwd=aWVwbFpxWnMrbzUrN0Nwb3ZtV0RiUT09

Meeting ID: 469 903 2903
Passcode: 450ZXL














    using System;
    using System.Collections.Generic;
    using System.ComponentModel;
    using System.Data;
    using System.Data.SqlClient;
    using System.Drawing;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows.Forms;

    namespace test_3
    {
    public partial class Form5 : Form
    {
        SqlConnection con = new SqlConnection("Data Source=localhost\\MSSQLSERVER01;Initial Catalog=warzer;Integrated Security=True");
        SqlCommand cmd;
        SqlCommand cmd2;
        SqlDataAdapter adapt;
        int ID = 0;
        int ID2 = 0;
        string name_t = "";
        string name_t2 = "";
        string time_for_send = DateTime.Now.ToString("yyyy:MM:dd");
        int totle_time1 = 0;
        int totle_time2 = 0;
        int totle_time3 = 0;
        public Form5()
        {
            InitializeComponent();
            DisplayData1();
            countingnames();
            countingallnames();
        }

        private void Form5_Load(object sender, EventArgs e)
        {

        }
        private void SearchData(string id)
        {
            con.Open();
            adapt = new SqlDataAdapter("SELECT * FROM R_table WHERE id LIKE '%" + id + "%'", con);
            DataTable dt = new DataTable();
            adapt.Fill(dt);
            dataGridView1.DataSource = dt;
            con.Close();
            countingnames();
        }

        private void DisplayData1()
        {
            con.Open();
            DataTable dt2 = new DataTable();
            adapt = new SqlDataAdapter("select * from R_table", con);
            adapt.Fill(dt2);
            dataGridView1.DataSource = dt2;
            con.Close();
        }
        private void countingnames()
        {
            int rowCount1 = dataGridView1.RowCount;
            rowCount1--;
            label_count1.Text = "Total Rows: " + rowCount1.ToString();
        }
        private void countingallnames()
        {
            con.Open();
            SqlCommand cmd = new SqlCommand("SELECT COUNT(*) FROM test_table", con);
            int count = (int)cmd.ExecuteScalar();
            con.Close();
            label_count2.Text = "Total Names: " + count.ToString();
        }
        private void FilterData()
        {
            // Create a dictionary to hold the filter conditions
            Dictionary<string, string> filters = new Dictionary<string, string>();

            // Add the selected filter values to the dictionary
            if (Box_stage.SelectedItem != null)
            {
                filters.Add("stage_R", Box_stage.SelectedItem.ToString());
            }
            if (Box_group_time.SelectedItem != null)
            {
                filters.Add("group_ev_R", Box_group_time.SelectedItem.ToString());
            }
            if (box_class.SelectedItem != null)
            {
                filters.Add("class", box_class.SelectedItem.ToString());
            }

            // Construct the SQL query
            string query = "SELECT * FROM R_table WHERE 1=1";
            foreach (KeyValuePair<string, string> filter in filters)
            {
                query += " AND " + filter.Key + " = @value";
            }

            // Execute the query with parameterized values
            using (SqlCommand cmd = new SqlCommand(query, con))
            {
                foreach (KeyValuePair<string, string> filter in filters)
                {
                    cmd.Parameters.AddWithValue("@value", filter.Value);
                }
                SqlDataAdapter adapter = new SqlDataAdapter(cmd);
                DataTable dt = new DataTable();
                adapter.Fill(dt);
                dataGridView1.DataSource = dt;
            }

            countingnames();
        }
        private void Box_stage_SelectedIndexChanged(object sender, EventArgs e)
        {
            FilterData();
        }

        private void Box_group_time_SelectedIndexChanged(object sender, EventArgs e)
        {
            FilterData();
        }

        private void box_class_SelectedIndexChanged(object sender, EventArgs e)
        {
            FilterData();
        }

        private void checkBox1_CheckedChanged(object sender, EventArgs e)
        {
            if (resetCheckBox.Checked)
            {
                Box_stage.SelectedItem = null;
                Box_group_time.SelectedItem = null;
                box_class.SelectedItem = null;

                DisplayData1();
                countingnames();
                resetCheckBox.Checked = false;
            }
        }

        

        private void textBox_search_KeyUp(object sender, KeyEventArgs e)
        {
            //// Check if the user pressed Enter
            //if (e.KeyCode == Keys.Enter)
            //{
            //    // Call SearchData method with ID value entered in textBox_search control
            //    SearchData(textBox_search.Text);
            //}
        }

        private void textBox_search_TextChanged(object sender, EventArgs e)
        {
            SearchData(textBox_search.Text);
        }

        private void dataGridView1_CellValueChanged(object sender, DataGridViewCellEventArgs e)
        {
            int rowIndex = e.RowIndex;
            if (e.RowIndex >= 0 && e.RowIndex < dataGridView1.Rows.Count)
            {
                ID2 = Convert.ToInt32(dataGridView1.Rows[e.RowIndex].Cells[1].Value.ToString());
                totle_time3 = Convert.ToInt32(dataGridView1.Rows[e.RowIndex].Cells[8].Value.ToString());
                cmd = new SqlCommand("update R_table set totle_time=@totle_time3 where ID=@id", con);
                con.Open();
                cmd.Parameters.AddWithValue("@id", ID2);
                cmd.Parameters.AddWithValue("@totle_time3", totle_time3);
                cmd.ExecuteNonQuery();
                con.Close();

                DisplayData1();
                countingnames();
            }
            
        }

        
    }
    }











//---------------------------------------------------------------------------//









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
