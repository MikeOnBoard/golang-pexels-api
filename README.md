# **Golang pexels api**
## **Project Overview**
The golang-pexels-api project is a Golang application that interfaces with the Pexels API to fetch high-quality stock images based on user-specified search terms. This project demonstrates a simple integration with an external API, providing a foundation for more complex applications that involve image retrieval or media galleries.

## **Project Structure**
```plaintext
golang-pexels-api/
├── main.go          # Core file to initialize and handle API requests and responses
├── go.mod           # Dependency and module management integrity verification
└── README.md        # Documentation with setup and usage instructions
```
### **File Descriptions**
- main.go
Contains the application's logic, including API request functions, JSON parsing, and result display. Key functions include ``getImages``, which handles the HTTP requests to the Pexels API and ``displayImages``, which prints the output in a user-friendly format.

- go.mod
Manage dependencies and module versions, specifying the required packages for HTTP requests and JSON parsing.

- README.md
This documentation file provides setup instructions, usage examples, and additional project information.

## **Requirements**
- Go version 1.18+
- Pexels API Key: A valid API key from Pexels is required to authenticate API requests.
## **Setup Instructions**
1.Clone the Repository

```bash
git clone https://github.com/MikeOnBoard/golang-pexels-api
cd golang-pexels-api
```
2.Install Dependencies
```bash
go mod tidy
```
3.Set Up the API Key

- Open ``main.go``.
- Replace any placeholder for the API key with your actual key in the ``Authorization`` header of the HTTP requests.

4.Run the Application

```bash
go run main.go
```
Enter a search term (e.g., "mountains"), and the application will retrieve matching images from Pexels, displaying their URLs and metadata.

## **Usage Instructions**
### **Example Execution**
Upon running the application, you will be prompted for a search term. After entering a keyword, the program retrieves relevant images from the Pexels API, and outputs results with the following information:

- Image Title
- Photographer's Name
- URL to the Image
Example output:

```bash
Enter search term: mountains
Results:
1. Mountain Range - Photo by John Doe (URL: https://pexels.com/photo/12345)
2. Snowy Mountains - Photo by Jane Smith (URL: https://pexels.com/photo/67890)
...
```
## **Pexels API Configuration**
1.Authentication
The application uses an ``Authorization`` header in each HTTP request, which includes the API key. This is set in the ``main.go`` file, under the request headers.

2.Request and Response

- Endpoint: ``https://api.pexels.com/v1/search``
- The application sends a GET request with the search term as a query parameter.
- Responses are JSON-formatted, containing image URLs, photographer details, and metadata.

3.Error Handling
Errors in API requests (e.g., invalid API key or network issues) are logged with a descriptive message.

## **Core Functions in main.go**
- getImages(searchTerm string)

  - Builds and sends a request to the Pexels API.
  - Parses the JSON response into a structure containing image details.
  - Returns a slice of image data objects or an error.
- displayImages(images []Image)

  - Loops through the list of images and prints their titles, photographers, and URLs in a structured format.
- *parseJSONResponse(response http.Response)

  - Unmarshals the JSON response body and extracts relevant fields like URL, Photographer, and ``Title``.
## **Troubleshooting**
- Invalid API Key: Ensure that the API key is correctly placed in main.go and has not expired.
- Network Issues: Confirm connectivity to the Pexels API endpoint. Try a different search term if requests time out.
- JSON Parsing Errors: Ensure Pexels API has not changed its response format, as changes could break the current parsing code.
## **Conclusion**
The golang-pexels-api project provides a straightforward example of interacting with the Pexels API in Go. This project serves as a basic template for developers looking to incorporate media search features in their applications. With minor modifications, it could be expanded to support other features, such as saving images locally, filtering based on image dimensions, or integrating more advanced search options.
