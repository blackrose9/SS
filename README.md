using System;

namespace School_System
{
    class Student
    {
        public Student()
        {
            get_studentdet();
        }
        public void get_studentdet()
        {
        
            int x;
            
            Console.WriteLine("How many students do you want to register?");
            x = Console.Read();
            Console.WriteLine(" Please register your students");

            string[] name = new string[x];
            int[] admino = new int[x];
            int[] year = new int[x];
            for (int i = 0; i < x; i++ )
            {
                //enter student details
                Console.WriteLine("Enter Student details");
                Console.Write("Enter Name: ");
                name[i] = Console.ReadLine();
                Console.WriteLine("Enter Admission Number: ");
                admino[i] = Console.Read();
                Console.WriteLine("Enter Academic year of student: ");
                year[i] = Console.Read();
                Console.Write('\n');

                Console.Read();
            }
        }

        
    }
    class Course
    {
        internal int course;

        public Course()
        {
            get_courseName();
        }

        public void get_courseName()
        {
            Console.Write("What course do you want to register? ");
            Console.WriteLine("1. BBIT ");
            Console.WriteLine("2. BIF/ICS ");
            Console.WriteLine("3. BTC ");
            Console.Write('\n');
            course = Console.Read();

            switch (course)
            {
                case 1:
                    Console.Write("Welcome to BBIT, you have to pay 180000");
                    break;
                case 2:
                    Console.Write("Welcome to BIF/ICS you have to pay 190000");
                    break;
                case 3:
                    Console.Write("Welcome to BTC you have to pay 180000");
                    break;
            }

        }
    }
    class Finance : Course
    {
        protected static double feesbbit = 180000;
        protected static double feesbif = 190000;
        protected static double feesbtc = 180000;
        public double bal, dep;

        public Finance()
        {
            pay();
            calculatefee();
            get_fees();
        }
        public void pay()
        {
            Console.Write(" Enter the amount you would like to pay  ");
            dep = Console.Read();
        }
        public void calculatefee()
        {
            if (course == 1)
            {
                bal = feesbbit - dep;
            }
            else if (course == 2)
            {
                bal = feesbif - dep;
            }
            else if (course == 3)
            {
                bal = feesbtc - dep;
            }
        }
        public void get_fees()
        {
            if (bal > 0)
            {
                pay();
            }
            else if (bal == 0)
            {
                Console.WriteLine("You have cleared your fees. good job!");
                Console.ReadKey();
            }
            else
            {

            }
        }

    }
    class Exam : Finance
    {
        public Exam()
        {
            estatus();
        }
        public void estatus()
        {
            if (bal == 0)
            {
                Console.WriteLine("You have cleared your fees, you re legible for exams.");
                Console.ReadKey();
            }
            else
            {
                Console.WriteLine("Go pay your fees. You are not legible for exams!");
            }
        }
    }
        
    class Program
    {
        static void Main(string[] args)
        {
            //variable for condition statements
            int choice;
            
A:            Console.Clear();
            Console.Write("Choose and option");
            Console.WriteLine("1. Register students");
            Console.WriteLine("2. Register for your courses");
            Console.WriteLine("3. Check fee balance");
            Console.WriteLine("4. Pay Fees");
            Console.WriteLine("5. Find out if you are liable for exams");
            choice = Console.Read();

            switch (choice)
            {
                case 1:
                    Student s = new Student();
                    s.get_studentdet();
                    break;
                case 2:
                    Course c = new Course();
                    c.get_courseName();
                    break;
                case 3:
                    Finance f = new Finance();
                    f.pay();
                    break;
                case 4:
                    Exam e = new Exam();
                    e.estatus();
                    break;
                case 5:
                    Finance q = new Finance();
                    q.get_fees();
                    break;
                default:
                    Console.WriteLine("You have entered an incorrect option! Try again.");
                    Console.ReadLine();
                    goto A; 
            }


            Console.ReadKey();
        }
    }
}
