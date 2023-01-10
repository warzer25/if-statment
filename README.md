 
         Console.ForegroundColor = ConsoleColor.White;
            DataTable emp = new DataTable("emo_t");
            emp.Columns.Add("id",typeof(int));
            emp.Columns.Add("name", typeof(string));
            emp.Columns.Add("dept");
            emp.Columns.Add("age", typeof(int));
            emp.Columns.Add("salry", typeof(double));

            emp.WriteXmlSchema("emp_Schema.xml");

            emp.Rows.Add(1, "ahmad", "IT", 20, 400);
            emp.Rows.Add(2, "hoz", "IT", 21, 500);
            emp.Rows.Add(3, "kaream", "kargary", 22, 600);
            emp.Rows.Add(4, "hassan", "karaba", 20, 700);
            emp.Rows.Add(5, "ali", "nursing", 21, 100);
            emp.Rows.Add(6, "lana", "IT", 22, 500);
            emp.Rows.Add(7, "majid", "IT", 24, 600);
            emp.Rows.Add(8, "barham", "kargary", 25, 800);
            emp.Rows.Add(9, "farhad", "karaba", 19, 300);
            emp.Rows.Add(10, "darya", "nursing", 24, 200);
            emp.Rows.Add(11, "ahmad", "IT", 200, 4000);
            emp.Rows.Add(12, "hoz", "IT", 210, 5000);
            emp.Rows.Add(13, "kaream", "kargary", 220, 6000);
            emp.Rows.Add(14, "hassan", "karaba", 200, 7000);
            emp.Rows.Add(15, "ali", "nursing", 210, 1000);
            emp.Rows.Add(16, "lana", "IT", 220, 5000);
            emp.Rows.Add(17, "majid", "IT", 240, 6000);
            emp.Rows.Add(18, "barham", "kargary", 250, 8000);
            emp.Rows.Add(19, "farhad", "karaba", 190, 3000);
            emp.Rows.Add(20, "darya", "nursing", 240, 2000);

            //while (true)
            //{
            //    Console.WriteLine("Enter employee data (type 'exit' to stop):");
            //    Console.Write("ID: ");
            //    string idInput = Console.ReadLine();
            //    if (idInput == "exit")
            //    {
            //        break;
            //    }
            //    int id = int.Parse(idInput);

            //    Console.Write("Name: ");
            //    string name = Console.ReadLine();

            //    Console.Write("Department: ");
            //    string dept = Console.ReadLine();

            //    Console.Write("Age: ");
            //    int age = int.Parse(Console.ReadLine());

            //    Console.Write("Salary: ");
            //    double salary = double.Parse(Console.ReadLine());

            //    emp.Rows.Add(id, name, dept, age, salary);
            //}
            
            //Console.ForegroundColor = ConsoleColor.Green;
            //Console.WriteLine("the table");
            //Console.ForegroundColor = ConsoleColor.White;
            
            //foreach (DataRow r in emp.Rows)
            //{
            //    Console.WriteLine("----------------------------------");
            //    Console.WriteLine(string.Format("{0,2} | {1,8} | {2,8} | {3,2} | {4,5}", r["id"], r["name"], r["dept"], r["age"], r["salry"]));
            //}






            //Console.ForegroundColor= ConsoleColor.Red;
            //Console.WriteLine("===================================================");
            
            //Console.ForegroundColor = ConsoleColor.Green;
            //Console.WriteLine("the table sorted by salry");
            //Console.ForegroundColor = ConsoleColor.White;
            
            //var r2 = emp.AsEnumerable();
            //var p2 = from e in r2 orderby e.Field<double>("salry") descending select e;

            //foreach (var rr2 in p2 )
            //{
            //    Console.WriteLine("----------------------------------");
            //    Console.WriteLine(string.Format("{0,2} | {1,8} | {2,8} | {3,2} | {4,5}", rr2["id"], rr2["name"], rr2["dept"], rr2["age"], rr2["salry"]));
            //}




            //Console.ForegroundColor = ConsoleColor.Red;
            //Console.WriteLine("===================================================");
            //Console.ForegroundColor = ConsoleColor.Green;
            //Console.WriteLine("the table sorted by age");
            //Console.ForegroundColor = ConsoleColor.White;
            //var r3 = emp.AsEnumerable();
            //var p3 = from e in r2 orderby e.Field<int>("age") descending select e;

            //foreach (var rr3 in p3)
            //{
            //    Console.WriteLine("----------------------------------");
            //    Console.WriteLine(string.Format("{0,2} | {1,8} | {2,8} | {3,2} | {4,5}", rr3["id"], rr3["name"], rr3["dept"], rr3["age"], rr3["salry"]));
            //}






            //Console.ForegroundColor = ConsoleColor.Red;
            //Console.WriteLine("===================================================");
            //Console.ForegroundColor = ConsoleColor.Green;
            //Console.WriteLine("the table deparent and age");
            //Console.ForegroundColor = ConsoleColor.White;
            //var k = emp.AsEnumerable();
            //var w = from e in k orderby e.Field<int>("age") descending group e by e.Field<string>("dept");

            //foreach (var x in w)
            //{
            //    Console.ForegroundColor = ConsoleColor.Blue;
            //    Console.WriteLine(x.Key);
            //    Console.WriteLine("==============");
            //    Console.ForegroundColor = ConsoleColor.White;
            //    foreach (var t in x)
            //    {
            //        Console.WriteLine("----------------------------------");
            //        Console.WriteLine(string.Format("{0,2} | {1,8} | {2,8} | {3,2} | {4,5}", t["id"], t["name"], t["dept"], t["age"], t["salry"]));
            //    }
                
            //}







            //Console.ForegroundColor = ConsoleColor.Red;
            //Console.WriteLine("===================================================");
            //Console.ForegroundColor = ConsoleColor.Green;
            //Console.WriteLine("the table deparent and salry");
            //Console.ForegroundColor = ConsoleColor.White;
            //var k2 = emp.AsEnumerable();
            //var w2 = from e in k2 orderby e.Field<double>("salry") descending group e by e.Field<string>("dept");

            //foreach (var x2 in w2)
            //{
            //    Console.ForegroundColor = ConsoleColor.Blue;
            //    Console.WriteLine(x2.Key);
            //    Console.WriteLine("==============");
            //    Console.ForegroundColor = ConsoleColor.White;
            //    foreach (var t2 in x2)
            //    {
            //        Console.WriteLine("----------------------------------");
            //        Console.WriteLine(string.Format("{0,2} | {1,8} | {2,8} | {3,2} | {4,5}", t2["id"], t2["name"], t2["dept"], t2["age"], t2["salry"]));
            //    }

            //}





            //Console.ForegroundColor = ConsoleColor.Red;
            //Console.WriteLine("===================================================");
            //Console.ForegroundColor = ConsoleColor.Green;
            //Console.WriteLine("the table salry and age");
            //Console.ForegroundColor = ConsoleColor.White;
            //var k3 = emp.AsEnumerable();
            //var w3 = from e in k3 orderby e.Field<int>("age") descending group e by e.Field<double>("salry");

            //foreach (var x3 in w3)
            //{
            //    Console.ForegroundColor = ConsoleColor.Blue;
            //    Console.WriteLine(x3.Key);
            //    Console.WriteLine("==============");
            //    Console.ForegroundColor = ConsoleColor.White;
            //    foreach (var t3 in x3)
            //    {
            //        Console.WriteLine("----------------------------------");
            //        Console.WriteLine(string.Format("{0,2} | {1,8} | {2,8} | {3,2} | {4,5}", t3["id"], t3["name"], t3["dept"], t3["age"], t3["salry"]));
            //    }

            //}









            Console.ForegroundColor = ConsoleColor.Red;
            Console.WriteLine("===================================================");
            Console.ForegroundColor = ConsoleColor.Green;
            Console.WriteLine("last nested group");
            Console.ForegroundColor = ConsoleColor.White;

            var k4 = emp.AsEnumerable();
            var w4 = from e in k4
                     group e by e.Field<string>("dept") into deptGroup
                     from sg in
                     (
                        from s in deptGroup
                        group s by s.Field<double>("salry")
                     )
                     select sg;
            foreach (var x4 in w4)
            {
                Console.ForegroundColor = ConsoleColor.Blue;
                Console.WriteLine(x4.Key);
                Console.WriteLine("==============");
                Console.ForegroundColor = ConsoleColor.White;
                foreach (var t4 in x4)
                {
                    Console.WriteLine("----------------------------------");
                    Console.WriteLine(string.Format("{0,2} | {1,8} | {2,8} | {3,2} | {4,5}", t4["id"], t4["name"], t4["dept"], t4["age"], t4["salry"]));
                }
            }





            Console.ReadLine();






























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
