MIT License

Copyright (c) 2017 Lifu Tao

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


function telephoneCheck(str) {
  var newStr=str.replace(/ /g,""); //set variable newStr to be str without spaces
  /*if it has te right front parenthesis, the right back parenthesis, the right dash,
  the right amount of numbers, and no letters or invalid signs return true
  */
//---if statement that checks every single function---
if(str.indexOf("-")===0) //if the 0 index of the number has a negative return false
  {
    return false;
  }

if (checkFrontParenthesis(newStr)&&checkBackParenthesis(newStr)&&checkDashSign(newStr)&&checkInvalidCharacters(newStr)&&checkNumberAndCountryCode(newStr))
{ //if all the functions return true, the number given is a valid number
  return true;
}
else { //if one or more of the functions return false, the number given is invalid and return false
  return false;
}
  function checkFrontParenthesis(number) //function to check the placement of a front parenthesis
  {
    if(number.indexOf("(")!==-1) //if there is a parenthesis in the number...
    {
      var firstParenthesisIndex=number.indexOf("(");//take the index value of the "("
      if(number[firstParenthesisIndex+4]!==")")//if the closing parenthesis does not match up, return false
      {
        return false;
      }
    }
    return true; /*default statement as "true", if the number does not
    contain a parenthesis or has it in the correct place then return true as it satisfies it */

  }
  function checkBackParenthesis(number) //function to check the placement of the back parenthesis
  {
    if(number.indexOf(")")!==-1) //if there is a back parenthesis in the number...
    {
      var backParenthesisIndex=number.indexOf(")"); //get the index of the back parenthesis
      if(number[backParenthesisIndex-4]!=="(") //check if the back parenthesis matches with the front parenthesis
      {
        return false; //if it doesn't return false
      }
    }
    return true; //if the back and front parenthesis match or there is no back parenthesis return true
  }

  function checkDashSign(number) //function to check the placement of "-"
  {
    if(number.indexOf("-")!==-1) //if there is a "-" in the number...
    {
      if(number.match(/-(?=[\d{3}|\d{4}])/g)===null) //if 3 or 4 consecutive integers do not follow the dash return false
      {
        return false; //if afer the dash it does not match 3 consecutive or 4 consecutive integeres return false
      }
    }
    return true; //if it does not have a dash or after the dash it matches 3 or 4 consecutive integers return true
  }

  function checkNumberAndCountryCode(number) //function to check the number given
  {
    number=number.replace(/[\D]+/g,""); //get rid of anything that is not [0-9]
    if(number.length===11&&number[0]==="1") //if the length of the number is 11 and country code is 1 return true
      {
        return true;
      }
    else if(number.length===10)//if the length of the number is 10 return true
      {
        return true;
      }
    return false; //all other outcomes return false
  }

  function checkInvalidCharacters(number) //function to check any alphabetic values in the number
  {
    if(number.match(/[A-Za-z]+/g)!==null) //if there is alphabetic values return false
    {
      return false;
    }
    if(number.indexOf("?")!==-1) //if there is a question mark in the number, return false
    {
      return false;
    }
    return true; //if it does not have a alphabetic value or a question mark return true
  }




}

telephoneCheck("-1 (757) 622-7382"); //function call 

