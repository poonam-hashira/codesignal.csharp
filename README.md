# C# - CodeSignal Questions & Answers

#### 1. How to return an array in C#?
```
using System;

namespace HelloWorld
{
	public class Program
	{
		public static void Main(string[] args)
		{
			Console.WriteLine("Return an Array: " + string.Join(" ", GetArray()));
		}
		
		static int[] GetArray() {
		  int [] arr = { 5, 10, 20, 25, 50};
		  return arr;
		}
	}
}
```

#### 2. Given an array of integers and return single result by spliting all its items into two arrays in C#.
```
using System;

namespace HelloWorld
{
	public class Program
	{
		public static void Main(string[] args)
		{
			  int[] originalArray = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
			  Console.WriteLine("Split an Array: " + string.Join(" ", originalArray));
			  SplitArray(originalArray);
		}
    
		static void SplitArray(int[] originalArray)
		{
			int[] firstHalf, secondHalf;
			int length = originalArray.Length;
			int halfLength = length / 2;
			
			firstHalf = new int[halfLength];
			secondHalf = new int[length - halfLength];
			
			Array.Copy(originalArray, 0, firstHalf, 0, halfLength);
			Array.Copy(originalArray, halfLength, secondHalf, 0, length - halfLength);
			
			Console.WriteLine("Return first array: " + string.Join(" ", firstHalf));
			Console.WriteLine("Return second array: " + string.Join(" ", secondHalf));
		}
	}
}
```

#### 3. Combine two arrays into one in C#.
```
using System;
using System.Linq;

namespace HelloWorld
{
	public class Program
	{
		public static void Main(string[] args)
		{
			CombineArray();
		}
		static void CombineArray()
		{
			int[] array1 = { 1, 2, 3 };
			int[] array2 = { 4, 5, 6 };
			Console.WriteLine("First array: " + string.Join(" ", array1));
			Console.WriteLine("Second array: " + string.Join(" ", array2));
			
			int[] combinedArray = array1.Concat(array2).ToArray();
			Console.WriteLine("Combined array: " + string.Join(" ", combinedArray));
		}
	}
}
```

#### 4. Split all the characters of a string into minimum number of SMS Messages possible in C#?
```
using System;
using System.Collections.Generic;


namespace HelloWorld
{
	public class Program
	{
		public static void Main(string[] args)
		{
			string inputMessage = "The term computer language is sometimes used interchangeably with programming language.[2] However, the usage of both terms varies among authors, including the exact scope of each. One usage describes programming languages as a subset of computer languages.[3] Similarly, languages used in computing that have a different goal than expressing computer programs are generically designated computer languages.";

			List<string> smsMessages = SplitIntoSMS(inputMessage);
			int index = 1;
			foreach (var sms in smsMessages)
			{
			    Console.WriteLine("Message: " + index);
			    Console.WriteLine(sms);
			    index++;
			}
		}
    
		static List<string> SplitIntoSMS(string message)
		{
			List<string> smsMessages = new List<string>();
			
			int maxLength = 160; // Standard SMS character limit
			int currentIndex = 0;
			
			while (currentIndex < message.Length)
			{
			    int remainingLength = message.Length - currentIndex;
			    int currentLength = Math.Min(remainingLength, maxLength);
			
			    string sms = message.Substring(currentIndex, currentLength);
			    smsMessages.Add(sms);
			
			    currentIndex += currentLength;
			}
			
			return smsMessages;
		}
	}
}
```

#### HAPPY CODING!!
