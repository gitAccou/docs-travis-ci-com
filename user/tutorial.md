package вуплр2;
import java.util.Scanner;
public class ВуПЛР2 {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        System.out.print("Введите номер задания: ");
        int n = VvodI(in);
        switch (n){
            case 1: Zadanie1(in); break;
            case 2:Zadanie2(in);break;
            case 3:Zadanie3(in);break;
            case 4:Zadanie4(in);break;
            case 5:Zadanie5(in);break;
        }
        
     
        in.close();
    }
    public static void Zadanie1(Scanner in){
        int a,b,c;
        System.out.print("Задание 1.\nВведите натуральное число a: ");
        a=VvodI(in);
        System.out.print("Введите натуральное число b: ");
        b=VvodI(in);
        System.out.print("Введите натуральное число c: ");
        c=VvodI(in);
         if ((a + b <= c) || (a + c <= b) || (b + c <=a)){
              System.out.print("Треугольник нельзя построить");
         }
         else if ((a == b) & (a == c) & (b == c)){
              System.out.print("Треугольник равносторонний");
         }else if ((a==b)||(a==c)||(b==c)) {
                   System.out.print("Треугольник равнобедренный");
              }
              else {
                  System.out.print("Треугольник иной");
              }
         
    }
    public static void Zadanie2(Scanner in){
        int a,b, max=0;
        System.out.print("\nЗадание 2.\nВведите натуральное число a: ");
        a=VvodI(in);
        System.out.print("Введите натуральное число b: ");
        b=VvodI(in);
        if (b>a){//делитель дыух чисел не будет больше меньшего из чисел
            for (int i=1;i<=a;i++){//перебор делителей
                if (a%i==0 && b%i==0 && i>max) max=i;//нахождение максимального
            }System.out.print("\nНаибольший делитель числа "+a+" и числа "+b+" равен "+max);
        }else{//если число a больше b
            for (int i=1;i<=b;i++){
                if (a%i==0 && b%i==0 && i>max) max=i;
            }System.out.println("\nНаибольший делитель числа "+a+" и числа "+b+" равен "+max);
        }
    }
    public static void Zadanie3(Scanner in){
        double x,y;
        System.out.print("\nЗадание 3.\nВведите число x: ");
        x=VvodD(in," "," ");
        System.out.println("\nПожалуйста, подождите пока высчитывается ряд.");
        y=Math.sin(x);//первое значение
        while(true){
            y=Math.sin(y);//последующие значения
            if (Math.abs(y)<Math.pow(10,-4)){//если значение меньше по модулю 10^-4,нужно подождать, лучше брать маленькое число
                System.out.println("\nЧисло меньше 10^-4: "+y);
                break;//выход из цикла
            }
        }
    }
    public static void Zadanie4(Scanner in){
        double m,f1=1,f2=1,f;
        System.out.print("\nЗадание 4.\nВведите число m>1: ");
        m = VvodD(in," больше 1 ","-.*|0|1");
        while(true){
            f=f1+f2;
            f1=f2; f2=f;
            if (f>m){
                System.out.println("\n"+f);
                break;
            } 
        }
    }
    public static void Zadanie5(Scanner in){
        int a,b;
        System.out.print("\nЗадание 5.\nВведите натуральное число a: "); 
        a = VvodI(in);
        System.out.println("Простые делители:");
        System.out.print("1 ");
        for (int i=2;i<=a;i++){
            b=0;
            if (a%i==0){//находим делитель 
                for (int k=2;k<=i/2;k++){//проверяем сколько делителей имеет делитель, кроме деления на единицу и на себя
                    if (i%k==0){
                        b++;
                    } 
                }
                if (b==0){//если делителей нет, кроме как на 1 и на само себя, то это простой делитель и нам подходит
                    System.out.print(i+" ");
                }
            }
        }        
    }
    
    //МЕТОДЫ ВВОДА
    public static int VvodI(Scanner in){//ввод целых чисел
        int chet;
        for ( chet=4;(!in.hasNextInt() || in.hasNext("-.*|0"))&&  chet>0;chet--){ //цикл,который отвечает за проверку
            if((chet-2)<0){//избегание лишнего считывания
                chet=0;
                break;
            }
            switch (chet-1){
                case 1: if (in.next().indexOf('.')!= -1){
                            System.out.println("Введите число через запятую, попытки не снимаются, поэтому осталась "+(chet-1)+" попытка.");
                        }else{
                            System.out.println("Введите численное значение больше нуля, осталась "+(chet-1)+" попытка.");
                        }break;
                case 2: if (in.next().indexOf('.')!= -1){
                            System.out.println("Введите число через запятую, попытки не снимаются, поэтому осталось "+(chet-1)+" попытки.");
                        }else{
                            System.out.println("Введите численное значение больше нуля, осталось "+(chet-1)+" попытки.");
                        }break;
                case 3: if (in.next().indexOf('.')!= -1){
                            System.out.println("Введите число через запятую, попытки не снимаются, поэтому осталось "+(chet-1)+" попытки.");
                        }else{
                            System.out.println("Введите численное значение больше нуля, осталось "+(chet-1)+" попытки.");
                        }break;
            }
        }
        if(chet<=0){ //проверка остаточных попыток
            System.out.println("Попытки закончились." );
            System.exit(0);
        }
        int k = in.nextInt();
        return k;
    }
    public static double VvodD(Scanner in, String sms,String ogr){//ввод вещественных чисел
        int chet;
        for ( chet=4;(!in.hasNextDouble() || in.hasNext(ogr))&&  chet>0;chet--){ //цикл,который отвечает за проверку
            if((chet-2)<0){//избегание лишнего считывания
                chet=0;
                break;
            }
            switch (chet-1){
                case 1: if (in.next().indexOf('.')!= -1){
                            System.out.println("Введите число через запятую, попытки не снимаются, поэтому осталась "+(chet-1)+" попытка.");
                        }else{
                            System.out.println("Введите численное значение"+ sms+",осталась "+(chet-1)+" попытка.");
                        }break;
                case 2: if (in.next().indexOf('.')!= -1){
                            System.out.println("Введите число через запятую, попытки не снимаются, поэтому осталось "+(chet-1)+" попытки.");
                        }else{
                            System.out.println("Введите численное значение" +sms+",осталось "+(chet-1)+" попытки.");
                        }break;
                case 3: if (in.next().indexOf('.')!= -1){
                            System.out.println("Введите число через запятую, попытки не снимаются, поэтому осталось "+(chet-1)+" попытки.");
                        }else{
                            System.out.println("Введите численное значение"+ sms+",осталось "+(chet-1)+" попытки.");
                        }break;
            }
        }
        if(chet<=0){ //проверка остаточных попыток
            System.out.println("Попытки закончились." );
            System.exit(0);
        }
        double k = in.nextDouble();
        return k;
    }
    
}

