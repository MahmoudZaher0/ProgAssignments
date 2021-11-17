using System;

namespace ConsoleApp11
{
    class Program
    {
        static void Main(string[] args)
        {
            string Z1 = " ", Z2 = " ", Z3 = " ";
            double i1 = 0, i2 = 0, i3 = 0;
            bool x; // Represent switch state 
            Console.WriteLine(" \n Mahmoud Reda Hamed Zaher \n Sec: 07  \n ID: 1000173830 \n ");
            Console.WriteLine("******************************************************");
            Console.WriteLine(" Type \"True\" if switch is closed  or \"False\" if open ");
            x = bool.Parse((Console.ReadLine()));
            Console.WriteLine("Enter first impedance value in \"(R+iX)\" form ");
            Z1 = Console.ReadLine();
            // take Z2 value if switch closed otherwise do not 
            if (x)
            {
                Console.WriteLine("Enter second impedance value in \"(R+iX)\" form ");
                Z2 = Console.ReadLine();
            }
          
            Console.WriteLine("Enter third impedance value in \"(R+iX)\" form ");
            Z3 = Console.ReadLine();

            Complexnum cmp = new Complexnum();
     
            cmp.Current_Clac(Z1, Z2, Z3, x, ref i1, ref i2, ref i3);

            Console.WriteLine(" first impedance current : " + i1);
            Console.WriteLine("second impedance current : " + i2);
            Console.WriteLine("third impedance current : " + i3);
            Console.ReadKey();
        }
    }
    class Complexnum
    {
        // Changes complex domain to ordinary numbers domain
        public void Change(string num , ref double real , ref double img) 
        {
            if (num.Contains("+i"))
            {
                real = double.Parse(num.Split(new string[] { "+i" }, StringSplitOptions.None)[0]);
                img =  double.Parse(num.Split(new string[] { "+i" }, StringSplitOptions.None)[1]);
                
            }
            else if (num.Contains("-i"))
            {
                real =  double.Parse(num.Split(new string[] { "-i" }, StringSplitOptions.None)[0]);
                img =  -double.Parse(num.Split(new string[] { "-i" }, StringSplitOptions.None)[1]);

            }
        }

        
    
        public void Current_Clac(string num1, string num2, string num3,bool x , ref double i1, ref double i2, ref double i3)
        {
            double r1 = 0, r2 = 0, r3 = 0, im1 = 0, im2 = 0, im3 = 0;
            double Rt = 0, IMt = 0, Zt = 0;
            double numinator, denominator = 0, Z1, Z2, Z3, Z12;
            Change(num1, ref r1, ref im1);
            Change(num2, ref r2, ref im2);
            Change(num3, ref r3, ref im3);
            Z1 = Math.Sqrt(r1 * r1 + im1 * im1);
            Z2 = Math.Sqrt(r2 * r2 + im2 * im2);
            Z3 = Math.Sqrt(r3 * r3 + im3 * im3);
            // if switch is closed calculate Ztotal with Z2 in calculation 
            if (x)
            {
                // Where  Z12 = z1*z2 / z1+z2 gives (r1 * r2 - im1 * im2) + i (r1 * im2 + r2 * im1) as numinator 
                //                              and (r1+r2)+i(im1+im2) as denomirator                                                  
                numinator = Math.Sqrt((r1 * r2 - im1 * im2) * (r1 * r2 - im1 * im2) + (r1 * im2 + r2 * im1) * (r1 * im2 + r2 * im1));
                denominator = Math.Sqrt((r1 + r2) * (r1 + r2) + (im1 + im2) * (im1 + im2));
                Z12 = numinator / denominator;
                Zt = Z12 + Z3;

                i3 = 220 / Zt;
                i1 = i3 * Z2 / denominator;
                i2 = i3 * Z1 / denominator;
                
            }
            // No need for Z2 in calculation
            else
            {
                Rt = r1 + r3;
                IMt = im1 + im3;
                Zt = Math.Sqrt(Rt * Rt + IMt * IMt);

                i3 = 220 / Zt;
                i1 = i3;
            }


        }

    }
}
