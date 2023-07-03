# API Testing Assignment

The purpose of this assignment is to write the Test Cases of the following APIs and automate them using Postman or any similar tool
  1. GET API - https://reqres.in/api/users/
     Based on the above information do the following -
     1. Write the possible test cases for the above API. Think of both positive and negative test cases
     2. Automate those cases using Postman or any other similar tool
     3. Store the information of user with id=4
    
  3. GET API - https://reqres.in/api/users/4
     Verify the response of this API matches the above stored information of id=4

# Documentation

In this assignment, we have added the above two requests in collection named, Users.
This colection contains requests from API https://reqres.in.
It contains the following requests:

- Get user list (/api/users/)
- Get user details with userID 4(/api/users/4)

**https://reqres.in/api/users**

The above request fetch the user list with details in the response body. The response is in JSON format and consistes of the following information:

page: This displays the number of pages the API has
per-page: This displays the number of users shown per page
total: This displays the total number of users
total_pages: This displays the total number of pages which are there in the API
data: This displays the user data. The user data is then consists of:
id: The unique identifier of the user
email: The email address of the user
first_name: The first name of the user
last_name: The last name of the user
avatar: A URL of the user's avatar image
The API responds with a status code 200 OK which indicates that the request was successful.

**Test Case**:

1. In the first and second test case, we are verifying the status code of the API is 200 and the status code name has a string OK.
2. Third test case depicts that the response time is less than 250ms.
3. In the forth, fifth, sixth and the seventh test case, we are validating that the API returns the required response headers. Sixth test verifies the Content-Type header is application/json; charset=utf-8.
4. Test case 8 verifies the page number of the API Response. Here, we have used pm.expect() function along with .to.eql assertion to validate our test case.
5. Test case 9 verifies the number of users shown per page. Here also, we have used pm.expect() function along with .to.eql assertion to validate our test case.
6. Test case 10 verifies the total number of users fetched from the API response using pm.expect() function and .to.eql assertion.
7. Test Case 11 depicts the total number of pages which are there in the API is 2, using pm.expect() function and .to.eql assertion.
8. Test case 12 validates the JSON Schema of the API Response. Here, we have created a JSON schema out of our response and we have validated JSON response with our JSON schema, and if anything related to the properties of this schema and JSON’s response doesn't match, the test will fail.
9. Test case 13-17 verifies that the data is not null, using pm.expect() function and .to.not.null assertion.
10. Test case 18 validates that the email format is correct. Here, we are reading each user email using map() and matching each of them with the regular expression using if condition. The function returns true if the email format is valid and false if not valid after raising an alert message.
11. Test case 19-24 verifies if the specific user data is correct or not. In this, we are traversing the JSON response from the response body and retrieving the value of each of the data property in a variable. Using pm.expect() function and .to.eql assertion, we are validating each user's data.
12. Test 25 and 26 verifies that the support field is present and the support url is https://reqres.in/#support-heading, matching with that received in the API response. In test 25, we are using pm.expect() and .to.have.property assertion for verifying if the Support property is present in the body or not.
13. Test case 27 verifies the support text is "To keep ReqRes free, contributions towards server costs are appreciated!" This test case also uses pm.expect() and .to.eql assertion.
14. Test Cases 28 to 32 defines the negative test cases:
    In test case 28, we are verifying to make sure that the endpoint does not return an unexpected status code.
    Test case 29 verifies the number of users shown per page is not more than 6. This test case uses pm.expect() and .not.to.be.above() assertion.
    Test case 30 verifies that the total number of users received in the response are not more than 12. This test case also uses pm.expect() and .not.to.be.above() assertion.
    Test case 31 verifies that the total number of pages which are there in the API is not more than 2. This test case too uses pm.expect() and .not.to.be.above() assertion.
    Test case 32 validates that the id is not zero. This test case uses pm.expect() and .not.to.eql() assertion.
    
There could be more negative test cases which are currently not in the scope of this API as this API is not intended for production use and the data returned is not real or persistent. It is primarily used for testing or showcasing API functionality. These test cases could be:

  1. Sending a GET request with an invalid user ID and ensuring that it returns an appropriate error response i.e., 404 - Not Found.
  2. Checking the API's behavior when the endpoint is incorrect or unavailable and verify that it returns a 404 - Not Found response.
  3. Validating that the API returns an appropriate error response e.g., 400 - Bad Request when invalid query parameters are provided.
  4. Testing the behaviour of the API by using unsupported http methods like PUT, DELETE, and make sure that is returns 405 - Method Not Allowed status.
  5. Checking the API's behavior when unauthorized access is attempted and verifying that it returns a 401 - Unauthorized response. This could also be considered as a security test case.
  6. Lastly, in the Tests, we are storing the user information of Id=4. We are storing the information in a collection level variable using pm.collectionVariables.set(). We will then access this stored user information in our upcoming requests.


**https://reqres.in/api/users/4**

The above request fecth the user details with Id as 4. The response is in the JSON format and consists of the following details:

	id: 4
	email: eve.holt@reqres.in
	first_name: Eve
	last_name: Holt
	avatar: https://reqres.in/img/faces/4-image.jpg

The API responds with a status code 200 OK which indicates that the request was successful.

Next, we have used the stored values (as in previous requests) in assertions within our test script to verify that the response of this API matches with the stored information of id=4. Here, we are accessing the set variable(in the previous request) in a variable user4 using pm.collectionVariables.get().
Now, since we want to validate the id, email, first_name, last_name and avatar against the value of a set variable, we extraxt the value of each of these fields from the response body and assign them to a responseValue variable in each of our tests.
Next, we are retrieving the value of the set variable in expectedValue variable in each of the tests and finally we will use pm.expect() function along with .to.eql() as assertion to compare responseValue with expectedValue. If they match, the test will pass. Else, the test will fail.
