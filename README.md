package week8;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.util.TreeSet;


public class EighteenDemo
{
public static void main(String[] args) throws IOException 
{
TreeSet<Student> list = new TreeSet<Student>();
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
BufferedWriter bw = new BufferedWriter(new FileWriter(new File("student.message")));
list.add(new Student(3, "xiao3", 21, 86));
list.add(new Student(4, "xiao4", 23, 85));
list.add(new Student(9, "xiao2", 25, 66));
list.add(new Student(2, "xiao2", 25, 76));


for(Student x:list)
{
System.out.println(x);
String line = x.toString();
bw.write(line);
bw.newLine();
bw.flush();
}
br.close();
bw.close();
}
}
class Student implements Comparable<Student>
{
private Integer id;
private String name;
private Integer age;
private Integer score;

public Student(Integer id, String name, Integer age, Integer i)
{
this.id = id;
this.name = name;
this.age = age;
this.score = i;
}


public int compareTo(Student stu)    //重写compareTo（）方法，让数据降序排序；
{
int num = id<stu.id?1:((id==stu.id)?0:-1);
if(num == 0)
{
num = age<stu.age?1:((age==stu.age)?0:-1);
if(num == 0)
{
int i = name.compareTo(stu.name);
if(i>0)
{ 
num = -1;
}
else if(i<0)
{
num = 1;
}
else
{
num = score<stu.score?1:((score==stu.score)?0:-1);
}
}
}
return num;
}

public String toString() 
{
return "学号：" + id + ", 姓名：" + name + ", 年龄=" + age
+ ", 成绩=" + score;
}  
}
