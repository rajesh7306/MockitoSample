# MockitoSample

				MOCKITO

Mockito can be used as a mocking framework in Android. It allows us to fake external interactions

different types of Test objects that can be created and used in Mockito.
Mockito mock() method
It is used to create mock objects of a given class or interface. Mockito contains five mock() methods with different arguments. When we didn't assign anything to mocks, they will return default values. All five methods perform the same function of mocking the objects.
Following are the mock() methods with different parameters:
o	mock() method with Class: It is used to create mock objects of a concrete class or an interface. It takes a class or an interface name as a parameter.
Syntax: <T> mock(Class<T> classToMock)
o	mock() method with Answer: It is used to create mock objects of a class or interface with a specific procedure. It is an advanced mock method, which can be used when working with legacy systems. It takes Answer as a parameter along with the class or interface name. The Answer is an enumeration of pre-configured mock answers.
Syntax: <T> mock(Class<T> classToMock, Answer defaultAnswer)
o	mock() method with MockSettings: It is used to create mock objects with some non-standard settings. It takes MockSettings as an additional setting parameter along with the class or interface name. MockSettings allows the creation of mock objects with additional settings.
Syntax: <T> mock(Class<T> classToMock, MockSettings mockSettings)
o	mock() method with ReturnValues: It allows the creation of mock objects of a given class or interface. Now, it is deprecated, as ReturnValues are replaced with Answer.
Syntax: <T> mock(Class<T> classToMock, ReturnValues returnValues)
o	mock() method with String: It is used to create mock objects by specifying the mock names. In debugging, naming mock objects can be helpful whereas, it is a bad choice using with large and complex code.
Syntax: <T> mock(Class<T> classToMock, String name)
Following code snippet shows how to use mock() method:     
ToDoService doService = mock(ToDoService.class); 

 when() method
It enables stubbing methods. It should be used when we want to mock to return specific values when particular methods are called. In simple terms, "When the XYZ() method is called, then return ABC." It is mostly used when there is some condition to execute.
Following code snippet shows how to use when() method:
    when(mock.someCode ()).thenReturn(5);
      thenReturn() is mostly used with the when() method.
verify() method
The verify() method is used to check whether some specified methods are called or not. In simple terms, it validates the certain behavior that happened once in a test.
spy() method
Mockito provides a method to partially mock an object, which is known as the spy method. When using the spy method, there exists a real object, and spies or stubs are created of that real object. If we don't stub a method using spy, it will call the real method behavior. The main function of the spy() method is that it overrides the specific methods of the real object.
Following code snippet shows how to use the spy() method:
List spyArrayList = spy(ArrayList.class);
reset() method
The Mockito reset() method is used to reset the mocks. It is mainly used for working with the container injected mocks. Usually, the reset() method results in a lengthy code and poor tests. It's better to create new mocks rather than using reset() method. That is why the reset() method is rarely used in testing.




      The signature of the reset() method is:
     public static <T> void reset(T ... mocks) {  
      MOCKITO_CORE.reset(mocks);  
  }  
Mockito doThrow() method
The signature of the doThrow() method is:
public static Stubber doThrow(Throwable toBeThrown) {  
       return MOCKITO_CORE.doAnswer(new ThrowsException(toBeThrown));  
    }  

 doCallRealMethod() method
It is used when we want to call the real implementation of a method. In other words, it is used to create partial mocks of an object.
The signature of the doCallRealMethod() method is:
public static Stubber doCallRealMethod() {  
       return MOCKITO_CORE.doAnswer(new CallsRealMethods());  
   }   
doAnswer() method
It is used when we want to stub a void method with a generic Answer type. 
The signature of the doAnswer() method is:
public static Stubber doAnswer(Answer answer) {  
        return MOCKITO_CORE.doAnswer(answer);  
    } 
times() method
It is used to verify the exact number of method invocations, which means it declares how many times a method is invoked. 
The signature of the times() method is:
public static VerificationMode times(int wantedNumberOfInvocations) {  
        return VerificationModeFactory.times(wantedNumberOfInvocations);  
 }  
never() method
It is used to verify that the interaction did not happen. 
The signature of the never() method is:
public static VerificationMode never() {  
        return times(0);  
 }  
calls() method
It allows a non-greedy verification in order. It can only be used with the inOrder() verification method.
The signature of the calls() method is:
public static VerificationMode calls( int wantedNumberOfInvocations ){  
       return VerificationModeFactory.calls( wantedNumberOfInvocations );  
 }  
only() method
It checks that the given method was the only invoked method. 
The signature of the only() method is:
public static VerificationMode only() {  
        return VerificationModeFactory.only();  
 }   
timeout() method
It allows Mockito to perform verification with a timeout. It instructs a verify to wait for a specific period of time for a particular interaction rather than to fail immediately. It may be useful for testing in existing situations.
The signature of the timeout() method is:
public static VerificationWithTimeout timeout(long millis) {  
        return new Timeout(millis, VerificationModeFactory.times(1));  
 }  
after() method
It allows Mockito to verify over a given period of time. We have already discussed that the after() method differs from the timeout() method.
The signature of the after() method is:
public static VerificationAfterDelay after(long millis) {  
        return new After(millis, VerificationModeFactory.times(1));  
 }  


Advantages and disadvantages
The advantages of Mockito are:
•	provides a huge amount of APIs to test classes and public methods;
•	the java documentation is well done and exhaustive, you can also find many references in the literature;
•	is a widely used framework in Android, in fact its use is recommended on developer.android.com.
Disadvantages:
•	The real limit of this framework is the lack of access to private methods or private attributes of a class;
•	It is not possible to create a fake of a static method;
•	It can lead to code change for testing purposes, e. g. forces you to create getters and setters to access private attributes of the class to be tested.
