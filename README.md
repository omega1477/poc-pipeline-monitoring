ddddUse a Lambda Expression in Java 
dddd
xxxxffffbbbcccccccqqq
Sign in to Developer VM as Admin by using Passw0rd! as the password.

Open the Eclipse IDE for Enterprise Java and Web Developers.

Create a Java project named JCS-004 that is configured to use JavaSE-1.8.

Expand this hint for guidance on creating a Java project.
On the File menu, select New, and then select Project.

Select Java Project, and then select Next.

In Project name, enter JCS-004.

In JRE, ensure that Use as an execution environment JRE is selected, select JavaSE-1.8, and then select Finish.

In the Open Associated Perspective message box, select Open Perspective.

If needed, close the Welcome tab in the IDE.

The Welcome tab

Go to D:\LabFiles, copy the src folder, and then paste it into the JCS-004 project in Package Explorer, overwriting the existing content.

Expand this hint for guidance on copying a project.
In File Explorer, go to D:\LabFiles.

Copy the src folder.

In Eclipse, in Package Explorer, right-click JCS-004, and then select Paste.

In the Overwrite JCS-004/src message box, select Overwrite All.

If you do not see this message box, select Cancel, and then try again.

Expand JCS-004, expand src, expand com.jcs, and then verify that the Movie, MovieDAO, MovieStore, and TestMovie files are available.

The following screenshot shows the project in Package Explorer:

Project in Package Explorer

When you paste the src folder into the JCS-004 project, you should see an Overwrite JCS-004/src message box. Select Overwrite All. If you do not see this message box, select Cancel, and then try again.

Open the Movie.java file, and then review the fields and the setter and getter methods.

The Movie class is what is known as a POJO, or a Plain Ol' Java Object. This is because it has instance variables—also known as fields—and setter and getter methods that match them, but not much else.

Open the MovieDAO.java file, review the constructor that takes a list of Movie objects, and then review the orderBy method that sorts a list.

Open the MovieStore.java file, and then review the movies list and the static getMovies method.

The MovieStore class builds a list of Movie objects that are returned by the getMovies method.

Open the TestMovie.java file, review the main method, and then review the printMovieList and findByDirector static methods.

You will use these methods to test the TreeSets in your code.

Confirm that you created a project named JCS-004.
Confirm that you copied the src folder, and then pasted the folder into the JCS-005 project.
In TestMovie, in the printMovieList method, declare a local variable named movieList of type List that takes a type argument of Movie.

Expand this hint for guidance on declaring a variable by using a type argument.
On the TestMovie.java tab, in the TestMovie class, in the printMovieList method, add the following code to declare the movieList variable:

List<Movie> movieList;
The following screenshot shows where to add the code:

Declare the movieList variable

When you use any of the classes that implement java.util.Collection, you should take advantage of generics and assign a type argument. Without a type argument, you will need to explicitly cast elements in the collection to their correct types. There are two ways that you can set up the type argument. You can explicitly define the type argument, or you can use a placeholder for the type argument when you instantiate the object.

To explicitly define the type argument—for example, an ArrayList that only contains objects of type String—you can declare and instantiate the ArrayList object by using the syntax List x = new ArrayList(). The string is defined on both sides of the equals sign.

Call the getMovies method of the MovieStore class, and then assign the output to the movieList variable.

Expand this hint for guidance on assigning a value to a variable.
On a new line, add the following code to instantiate the movieList variable:

movieList = MovieStore.getMovies();
The following screenshot shows where to add the code:

Instantiate the movieList

Print each element in movieList by using the forEach method of the list and a method reference to the println method.

Expand this hint for guidance on using the forEach method of a list.
On a new line, add the following code to print each element of the list:

movieList.forEach(System.out::println);
The following screenshot shows where to add the code:

The forEach method of the list

In a lambda expression, if you only need to call a method, you can use a method reference. Method references are generally in the form of class_name::method_name. The method may or may not be static as long as the lambda expression can figure out at run time what would be calling it and what, if any, arguments are to be passed in.

In this Challenge Lab, the println method is static and is being called by the static variable System.out. Normally, you would have to pass in what you wanted to print, but in this case, the forEach method handles that for you.

In the main() method, call the static printMovieList method of the TestMovie class.

Expand this hint for guidance on calling a static method.
Import the java.util.List interface.

Expand this hint for guidance on importing an interface.
After the package declaration, add the following code to import the java.util.List interface:

import java.util.List;
The following screenshot shows where to add the code:

The import statements

You place the import statements after the package declaration and before the class declaration.

Save the file, and then verify that there are no errors.

Expand this hint for guidance on verifying that there are no errors.
On the File menu, select Save.

On the Problems tab, verify that there are no errors.

The Problems tab

Run the TestMovie class.

Expand this hint for guidance on running a class.
In Package Explorer, right-click TestMovie.java, select Run As, and then select Java Application.
The following screenshot shows the expected result:

The expected result

Confirm that you declared a local variable named movieList of type List.
Confirm that you initialized the movieList by using a static method call to getMovies.
Confirm that you printed each item in movieList by using the forEach method.
Confirm that you imported the List interface.
Create a functional interface

In the com.jcs package, create an interface named Tester that takes a type parameter argument of T.

Expand this hint for guidance on creating an interface.
Right-click com.jcs, select New, and then select Interface.

In Name, enter Tester<T>, and then select Finish.

The following screenshot shows the interface declaration:

The interface declaration

Annotate Tester by using the FunctionalInterface annotation.

Expand this hint for guidance on adding an annotation to an interface.
Immediately before the interface declaration, add the following line of code:

@FunctionalInterface
The following screenshot shows where to add the code:

Add the FunctionalInterface annotation

Functional interfaces are interfaces that have at most one abstract method. If you use the FunctionalInterface annotation, you are telling the compiler to enforce that there is only one abstract method.

In the Tester interface, declare an abstract method named test that takes a parameter of type T and returns a boolean data type.

Expand this hint for guidance on declaring an abstract method.
In the interface, add the following code to declare a method that returns a boolean data type:

boolean test(T t);
The following screenshot shows where to add the code:

Declare a method in an interface

If a method in an interface is not declared to be default or static, then it is implicitly abstract. All methods in an interface are implicitly public.

Save the file, and then verify there are no errors.

Confirm that you created a functional interface named Tester.
Implement a functional interface in a lambda expression

In the MovieDAO class, declare a new method named findBy that takes a parameter named t of type Tester that has a type argument of Movie and returns a List of Movie objects.

Expand this hint for guidance on declaring a method that takes a parameter and returns a collection.
Switch to the MovieDAO class.

At the end of the class, add the following code to declare a new public method that takes a parameter and returns a collection of Movie objects:

public List<Movie> findBy(Tester<Movie> t){
}
The following screenshot shows where to add the code:

The findBy method

The findBy method takes an instance of the Tester interface. In an upcoming step in this task, you will implement Tester as a lambda expression and pass it in when calling this method.

Declare a local variable named temp of type List that takes a type argument of Movie.

Instantiate temp as an ArrayList by using diamond notation.

Expand this hint for guidance on instantiating an object by using diamond notation.
Add the following code to instantiate temp as an ArrayList by using diamond notation:

temp = new ArrayList<>();
The following screenshot shows where to add the code:

Instantiate an object by using diamond notation

Starting with Java SE 7, when you are defining the type argument, you can use diamond notation so that you do not need to redefine the type argument. In this case, you declare and instantiate the variable by using the syntax List x = new ArrayList<>(). The diamond notation means that you do not need to redefine the type argument when you instantiate the object—you use the syntax <> as a placeholder.

Define a for-each loop that iterates over the instance variable movieList by using a counter variable named m of type Movie.

Expand this hint for guidance on defining a for-each loop.
Add the following code to define a for-each loop:

for(Movie m: movieList){ 
}
The following screenshot shows where to add the code:

The for loop

In the for-each loop, define an if statement that evaluates if the test method of t returns true.

Expand this hint for guidance on defining an if statement.
In the for-each loop, add the following code to define an if statement:

if(t.test(m)){

}
The following screenshot shows where to add the code:

The if statement

In the if statement, add the Movie m to the temp list.

After the for-each loop, return temp.

Expand this hint for guidance on returning a value in a method.
After the for-each loop, add the following code to return the temp list:

return temp;
The following screenshot shows where to add the code:

The return value

Import the java.util.ArrayList class.

Save the file, and then verify that there are no errors.

In the TestMovie class, in the findByDirector method, declare a local variable named movieList of type List that takes a type argument of Movie, call the getMovies method of the MovieStore class, and then assign the return value to the movieList variable.

Declare a local variable named dao of type MovieDAO, instantiate the variable by using the MovieDAO constructor, and then pass in movieList as the argument.

Expand this hint for guidance on calling a constructor that takes an argument.
Add the following code to instantiate the dao variable:

MovieDAO dao = new MovieDAO(movieList);
The following screenshot shows where to add the code.

Call a constructor that takes an argument

Retrieve all of the movies directed by Hayao Miyazaki by using a lambda expression and the getDirector method of the Movie object named m, and then assign the result to a new variable named t of type Tester.

Expand this hint for guidance on defining a lambda expression.
Add the following code to retrieve movies by a specified director by using a lambda expression:

Tester<Movie> t = m -> m.getDirector().equals("Hayao Miyazaki");
The following screenshot shows where to add the code.

Create the lambda expression

When you use a lambda expression in Java, you are writing the content of an otherwise abstract method. The format of a lambda expression is (parameters) -> functionality.

Because you know the method that must be overridden, including the arguments and the return of the method, Java can figure out those values for you. You pass in parameters on the left, use the lambda symbol ->, and then on the right, you define the functionality that you want. If there is only one parameter, you do not need parentheses around it.

Usually, you pass the lambda expression directly in place of the functional interface. For clarity, you separate the creation of the lambda expression and the use of the expression into two steps.

Call the findBy method of dao, pass in the Tester named t, and then assign the return value to a new List named byDirector that has a type argument of Movie.

Print the results by using the forEach method of byDirector.

Replace the code in the main() method with a call to the static findByDirector method of TestMovie.

Save the file, and then verify that there are no errors.

Run the TestMovie class.

The following screenshot shows the expected result:

Results of findByDirector

Confirm that you defined a findBy method in MovieDAO.
Confirm that you iterated over the movieList and added each element that returned true to a new list.
Confirm that you created a findByDirector method in TestMovie.
Confirm that you used a lambda expression to find movies by a given director.
Confirm that you printed the movies that were found.
Use a lambda expression that takes two parameters

In the TestMovie class, in the findByDirector method, delete the line of code that prints the byDirector list.

Compare the titles of m1 and m2 by using a lambda expression, the getTitle method, and the compareTo method, and then assign the output to a variable named comp of type Comparator that takes a type argument of Movie.

Expand this hint for guidance creating a lambda expression that uses two parameters.
Add the following code to compare the titles of m1 and m2 by using a lambda expression:

Comparator<Movie> comp = (m1, m2) -> m1.getTitle().compareTo(m2.getTitle());
The following screenshot shows were to add the code:

Implement a Comparator type as a Lambda expression

You will use this comparator to compare two Movie objects and order them alphabetically by movie title.

Import the java.util.Comparator interface.

The Comparator interface is a functional interface. It has one abstract method named compare that takes two parameters of the same type and returns an int. In this case, you want to compare two String objects, so you can use the compareTo method of the String type to do most of the work for you.

Call the orderBy method of dao, pass in byDirector and comp as parameters, and then assign the results to byDirector.

Print the results by using the forEach method of byDirector.

Save the file, and then verify that there are no errors.

Run the TestMovie class.

The following screenshot shows the expected result:

The result of the findByDirector method

Confirm that you defined a comparator by using a lambda expression to compare movie titles.
Confirm that you called the orderBy method in MovieDAO.
Confirm that you imported the Comparator interface.
Confirm that you printed each item in byDirector in alphabetical order by movie title.
Congratulations, you have completed the Use a Lambda Expression in Java challenge.

You have accomplished the following:

Used a method reference.
Created a functional interface.
Defined a method by using a lambda expression.
Defined a lambda expression that takes two parameters.
Your feedback is important!
As you end your Challenge Lab, please take a few minutes to complete the short survey that will appear in the next window.

Alternatively, you may provide your feedback directly to Challenge Labs feedback.

Be sure to check out the other Challenge Labs in this series:
GUIDED CHALLENGE: Create and Manipulate an ArrayList in Java
GUIDED CHALLENGE: Sort Objects by Using a Comparator and a TreeSet
GUIDED CHALLENGE: Create and Manipulate a Map in Java
GUIDED CHALLENGE: Use Streams in Java
