# Generics

The requirement is i have to store the text data which user enters 
I took abstract class of Employee. so, that we cannot create object 

    abstract class Employee 
 
 In order to enter the detailes and to display the detailes i took two methods with the help of them we can create and display the detailes which user enters
 and also at last i took another methos to raise the salary. when , user wants to raise the salary 
 
     String name, desig;
        int age, sal;
        public Employee() 
        {
          try
          {
          BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
          System.out.print("\n Enter Name ");
          name = br.readLine();
          System.out.print("\nEnter Age : ");
          age = Integer.parseInt(br.readLine());
          }
          catch(Exception e)
          {

          }
        }

        public void display()
        {
          System.out.println("Name is :"+name);
          System.out.println("Age is :"+age);
          System.out.println("Salary is :"+sal);
          System.out.println("Designation is :"+desig);
        }

        public abstract void raiseSalary();
    }
   
 To enter the detailes of the Clerk, Manager and Programmer i took three classes as final to restrict the inherit of the classes
 
     final class Manager extends Employee 
    {
        public Manager() 
        {
          desig = "Manager";
          sal = 4000;
        }
        public void raiseSalary() 
        {
          sal += 20000;
        }
    }
    final class Programmer extends Employee 
    {
      public Programmer() 
      {
        desig = "Programmer";
        sal = 9000;
      }
      public void raiseSalary() 
      {
        sal += 50000;
      }
    }
 
 To store the text, i gave path of the file which it stores the user guven data
 
     PrintWriter writer = new PrintWriter(new FileOutputStream("C:/Users/anilp/Desktop/java/Employee Data Store/Data_Store.txt",true));
     
To read from console and to take the input i used buffer reader

     
     BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        ArrayList<Employee> employee = new ArrayList<Employee>();
        
  to choose the options i gave initial choices as zero      

    int outerMenuChoice = 0, innerMenuChoice = 0;
	
		do {
				System.out.print("\n\n1.CREATE\n2.DISPLAY\n3.RAISESALARY\n4.EXIT\nENTER YOUR CHOICE: ");
				outerMenuChoice = Integer.parseInt(br.readLine());


And to avoid the duplicate data entry and for the choice selection 



    switch(innerMenuChoice) 
                  {
                    case 1: emp = new Clerk();
                    break;
                    case 2: emp = new Manager();
                        break;
                    case 3: emp = new Programmer();
                    break;
                    case 4: break;
                    default: System.out.print("\n\ninvalid entry...!");
                        break;
                  }
                  if(innerMenuChoice == 1 || innerMenuChoice == 2 || innerMenuChoice == 3) 
                  {
                    boolean existing = false;
                    for( Employee k : employee) 
                    {
                      if(k.name.equals(emp.name) && k.age == emp.age) 
                      {
                        System.out.print("\nRecord already exists...");
                        existing = true;
                        break;
                      }
                    }
                    if(!existing) 
                    {
                      employee.add(emp);
                      writer.println("______________________________");
                      writer.println("Name is :"+emp.name);
                      writer.println("Age is :"+emp.age);
                      writer.println("Sal is :"+emp.sal);
                      writer.println("Desig is :"+emp.desig);
                      writer.println("______________________________");
                      writer.flush();

                    }
                   }
              }	while(innerMenuChoice != 4);
                break;
              }
            case 2: 
              {
              if(employee.size() == 0) 
                {
                  System.out.print("\n\nNorecords found.....?");
                  break;
                }
              for(Employee e:employee)e.display();
              break;
              }
            case 3: 
              {
              if(employee.size() == 0) 
                {
                  System.out.print("\n\nNorecords found.....?");
                  break;
                }
              for(Employee e:employee) e.raiseSalary();
                  System.out.print("\n\nSalary raised...");
                  break;
              }
            case 4: System.out.print("\nExiting....!");
                break;
            default: System.out.print("\nInvalid choice....$");

            }
        }	while(outerMenuChoice != 4);


        }catch(Exception e)
        {
               System.out.println(e);
        }
      }
    }
