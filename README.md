# java



```java

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Date;

public class App {
	
	private ArrayList<String> weekdays = new ArrayList<String>( 
            Arrays.asList("SUNDAY", 
	                       "MONDAY", 
	                       "TUESDAY", 
	                       "WEDNESDAY", 
	                       "THURSDAY", 
	                       "FRIDAY", 
                           "SATURDAY")); 

    SimpleDateFormat sdf = new SimpleDateFormat("yyyy/MM/dd");
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		 
	
       
		App app = new App();
	

		

//		System.out.println(	app.getLastSunday(0));
//		System.out.println(	app.getLastSunday(1));
//		System.out.println(	app.getLastSunday(2));
//		System.out.println(	app.getLastSunday(3));
//		System.out.println(	app.getLastSunday(4));
		

		ArrayList<String> preOneWeekdays = app.getDaysFromSunday(	app.getLastSunday(1));
		ArrayList<String> preTwoWeekdays = app.getDaysFromSunday(	app.getLastSunday(2));
		ArrayList<String> preThreeWeekdays = app.getDaysFromSunday(	app.getLastSunday(3));
		ArrayList<String> preFourWeekdays = app.getDaysFromSunday(	app.getLastSunday(4));

		
      
   
	}
	
	private String getDay(Date date){

	    SimpleDateFormat simpleDateFormat = new SimpleDateFormat("EEEE");
	    //System.out.println("DAY "+simpleDateFormat.format(date).toUpperCase());                       
	    return simpleDateFormat.format(date).toUpperCase();
	}
	
	private String getLastSunday(int weeks ){

		Date today =  new Date() ;
		System.out.println(today);
		String weekday = this.getDay(today);
		int index = weekdays.indexOf(weekday) ; 

		long diff = (1000L * 60 * 60 * 24 * (index+ (weeks*7) ) );

	    long day =  today.getTime() - diff ;
	    

		System.out.println(new Date(day));
	    return sdf.format(new Date(day));
	}
	
	private ArrayList <String>  getDaysFromSunday(String sundayStr){
		ArrayList <String> list = new ArrayList <String>();
		Date sunday;
		list.add(sundayStr);
		try {
			sunday = sdf.parse(sundayStr);
			for(int i = 1 ; i <7 ; i++)
			{
				 long day = sunday.getTime() + (1000* 60 * 60 * 24 * i) ;
				 String dayStr = sdf.format( new Date(day));
				 list.add(dayStr);
			}
			
		} catch (ParseException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

	    
	    return list;
	}

}


```
