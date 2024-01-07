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

#### 2. Given an array of integers, Split all the items into two arrays then return single array by combining first & second splitted arrays in C#.
```
namespace HelloWorld
{
	public class Program
	{
		public static void Main(string[] args)
		{
			  int[] originalArray = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
			  Console.WriteLine("Original Array: " + string.Join(" ", originalArray));
			  SplitArray(originalArray);
		}
    
		static void SplitArray(int[] originalArray)
		{
			int[] firstHalf, secondHalf;
			int length = originalArray.Length;
			int halfLength = length / 2;

			// Spliting Array
			firstHalf = new int[halfLength];
			secondHalf = new int[length - halfLength];
			
			Array.Copy(originalArray, 0, firstHalf, 0, halfLength);
			Array.Copy(originalArray, halfLength, secondHalf, 0, length - halfLength);
			
			Console.WriteLine("Splited first array: " + string.Join(" ", firstHalf));
			Console.WriteLine("Splited second array: " + string.Join(" ", secondHalf));

			// Combining Array
			int[] combinedArray = firstHalf.Concat(secondHalf).ToArray();
			Console.WriteLine("Combined array: " + string.Join(" ", combinedArray));
		}
	}
}
```

#### 3. Split all the characters of a string into minimum number of SMS Messages possible in C#?
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

#### 4. Given a string sentence and count the numbers of words which contain triple repeating letters i.e. the same letter appearing at least three times. Words in the sentence are a sequence of english letters surrounded by whitespace characters. Note letters should be counted in a case-insensitive manner using c#.
```
// Online C# Editor for free
// Write, Edit and Run your C# code using C# Online Compiler

using System;
using System.Linq;

public class HelloWorld
{
    public static void Main(string[] args)
    {
        string sentence = "Applep is poooping me in sentence goes here.";

        int count = CountWordsWithTripleRepeatingLetters(sentence);
        
        Console.WriteLine($"Number of words with triple repeating letters: {count}");
    
    }
    
    static int CountWordsWithTripleRepeatingLetters(string sentence)
    {
        // Split the sentence into words
        string[] words = sentence.Split(new char[] { ' ', '\t', '\n', '\r' }, StringSplitOptions.RemoveEmptyEntries);
        // ["Applep", "is", ..]

        int count = 0;

        foreach (var word in words)
        {
            if (HasTripleRepeatingLetters(word))
            {
                count++;
                Console.WriteLine($"Matched word: {word}");
            }
        }

        return count;
    }

    static bool HasTripleRepeatingLetters(string word)
    {
        // Convert the word to lowercase for case-insensitive comparison
        string lowercaseWord = word.ToLower();

        // Check if any character appears at least three times in the word
        return lowercaseWord.GroupBy(c => c).Any(group => {
            if (group.Count() >= 3) {
                Console.WriteLine("\n");
                Console.WriteLine("repeating letters: " + group.Key);
            }
            return group.Count() >= 3;
            }
        );
    }
}
```

#### 5. You are given an array of uppercase and lowercase of english letters recording representing a sequence of letters typed by the user. Your task is to count the number of times that the user changed keys while typing the sequence, considering the uppercase and lowercase letter or a given letter require the user to press same letter key (Ignoring modifiers like Shift or Caps Lock). For example, typing 'W' and 'w' require the user to press the same key, whereas typing 'W' and 'E' or typing 'W' and 'e' require the user to change keys using c#.
```
// Online C# Editor for free
// Write, Edit and Run your C# code using C# Online Compiler

using System;
using System.Linq;

public class HelloWorld
{
    public static void Main(string[] args)
    {
        string sequence = "aAbBCcdDEe";

        int keyChanges = CountKeyChanges(sequence);

        Console.WriteLine($"Number of key changes: {keyChanges}");
    
    }
    
    static int CountKeyChanges(string sequence)
    {
        if (string.IsNullOrEmpty(sequence) || sequence.Length == 1)
        {
            return 0; // No key changes for an empty or single-character sequence
        }

        int changes = 0;

        // Convert the sequence to lowercase for case-insensitive comparison
        sequence = sequence.ToLower();

        // Check for key changes
        for (int i = 1; i < sequence.Length; i++)
        {
            if (sequence[i] != sequence[i - 1])
            {
                Console.WriteLine($"changed key from {sequence[i - 1]} to {sequence[i]}");
                changes++;
            }
        }

        return changes;
    }
}
```

#### HAPPY CODING!!
