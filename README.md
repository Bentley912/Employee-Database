# Employee-Database

This is another project from my coding bootcamp. This week we were working on Firebase and data persistence. 

Our assignment was to create an employee database that was connected to Firebase and updated in real time. We also were required to use Moment.js to calculate the months worked of each employee. 

Front - End: We built the front-end with Bootstrap. This was a simple layout that used a Jumbotron and two Panels, one with a table inside and one panel that had input groups. The challenge here was to take user input on the front end and do something with it on the back end. How do we take user input and push that into our Firebase database. 

Back-End: Our back-end was Jquery. We started by initializing our database. The obvious step was to trigger our back-end action on the Submit button click. We began with making sure that we could populate our table with the user input. We created a function:

function addEmployee(emp){
 var tBody = $("<tbody>");
 var newRow=$("<tr>");
 tBody.append(newRow);

 var startDate = moment(new Date(emp.startDate));
 var monthsWorked = parseInt(startDate.diff(moment(),'months')*-1);
 $("#employees").append(tBody);
 newRow.append("<td>"+
   emp.name+"</td><td>"+
   emp.role+"</td><td>"+
   emp.startDate+"</td><td>"+
   monthsWorked+"</td><td>$"+
   emp.rate+"</td><td>$"+monthsWorked*emp.rate+"</td>"
 )
}


This allowed us to resue that function later on. 

Our second step was to create a "Child_added" event that would allow us to push our user input into Firebase. Inside of this event, we were able to reuse our addEmployee(). Originally, when we added the child_added event listener, we were pushing the input values twice. One with each event. We evenetually found out that we were calling the input to be pushed twice - once with button submittal and then once with the child_added event. It was a quick fix. 

This project was done in apporximately 3 hours. In the near future, I would like to add a delete function. 

Overall, this was my first time using a database. I am also starting to realize how closely front-end and back-end devs have to work together to create a seamless application. 
