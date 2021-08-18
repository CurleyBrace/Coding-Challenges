# Coding-Challenges
This repo will be full of challenges I've either submitted during the application process or used to study to prepare and sharpen my skills! Feel free to browse using either the table of contents listed below which also give you a small explaination of what each project does, or if you'd like just wonder through either folder until you find something that interests you. Every coding challenge will have both a source code folder and an executable application so that you can test and see the result without needing to download or publish it yourself.


## Table of Contents
* ### NameSearch Challenge: [Application](https://github.com/CurleyT/NameSearch/tree/main/NameSearch_Application) | [Source](https://github.com/CurleyT/NameSearch/tree/main/NameSearch_SourceCode)
  * This code allows you to parse through a chunk of text and encrypt any instances of items from a designated list by replacing each character in that item with an 'X', making something like "Jacob" become "XXXXX". Code added after submission allows you to extend the characters it will check each text block for after splitting (i.e. periods, commas, etc..)
  * Code Snippet: 
 ```
 string[] textArray = textChunk.Split(" ");                                                  //Splitting textChunk into String Array at each space
            foreach (string name in names)                                                              //Parsing through names List
            {                                                                                           
                for (int i = 0; i < textArray.Length; i++)                                              //Parsing through text Array
                {                                                                               
                    string currentWord = textArray[i].ToLower();                                        //Temporary container for String from Current Array Position
                    string trimmedEnd = "";

                    //char[] charExceptions = { ',', '.', '?', '!', '\n' };                             //Changes made after submission to make the program function more cleanly and to increase scalability
                    //foreach(char exceptions in charExceptions)                                        //This allows you to set different character exceptions when parsing through text chunk data
                    //{                                                                                 //to ensure that everything is properly added back after the comparison between the current text
                    //    if (currentWord.Contains(exceptions)) {                                       //and the name that it is comparing to
                    //        trimmedEnd += exceptions;
                    //        currentWord.Trim(exceptions);
                    //        break;
                    //    }
                    //}
                    if (currentWord.Contains(",") == true || currentWord.Contains("."))                 //Checking temporary container for commas
                    {
                        trimmedEnd = (currentWord.Contains(",") == true) ? "," : ".";                   //Ternary Operator to check which symbol it contains and store that symbol between periods or commas
                        currentWord = currentWord.Trim(',', '.');                                       //Will trim either period or comma from the name
                    }
                    if (name.ToLower() == currentWord)                                                  //Checking name against trimmed word in current position of array
                    {
                        string replaceName = "";                                                        //Temporary Variable to hold 'X's
                        for (int x = 0; x < name.Length; x++)                                           //Traveling through the name
                        {
                            replaceName += "X";                                                         //Adding 'X' to our temporary value for each character in name
                        }
                        replaceName += trimmedEnd;                                                      //Adding whatever was trimmed off of our temporary container currentWord
                        textArray[i] = replaceName;                                                     //Replacing the current position in the array with our altered name
                    }
 ```
