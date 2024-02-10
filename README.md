# Go client
The OpenSearch Go client lets you connect your Go application with the data in your OpenSearch cluster. This getting started guide illustrates how to connect to OpenSearch, index documents, and run queries. For the client’s complete API documentation and additional examples, see the Go client API documentation.

For the client source code, see the opensearch-go repo.

## Setup
If you’re starting a new project, create a new module by running the following command:

go mod init <mymodulename>

To add the Go client to your project, import it like any other module:

go get github.com/opensearch-project/opensearch-go

Connecting to OpenSearch
To connect to the default OpenSearch host, create a client object with the address https://localhost:9200 if you are using the Security plugin:

client, err := opensearch.NewClient(opensearch.Config{
        Transport: &http.Transport{
            TLSClientConfig: &tls.Config{InsecureSkipVerify: true},
        },
        Addresses: []string{"https://localhost:9200"},
        Username:  "admin", // For testing only. Don't store credentials in code.
        Password:  "admin",
    })
Copy
If you are not using the Security plugin, create a client object with the address http://localhost:9200:

client, err := opensearch.NewClient(opensearch.Config{
        Transport: &http.Transport{
            TLSClientConfig: &tls.Config{InsecureSkipVerify: true},
        },
        Addresses: []string{"http://localhost:9200"},
    })
