# Golang GraphQL MongoDB CRUD Project

This repository contains the code for a CRUD application built with **Golang**, **GraphQL**, and **MongoDB**.

This project is demonstrated in my YouTube video (with nearly the same name), and showcases how to build a full-featured backend using GraphQL in Golang.

---

## 🛠 Project Initialization Steps

Follow the steps below to set up the project:

1. **Create a new project folder**  
   ```bash
   mkdir gql-yt && cd gql-yt
   ```

2. **Initialize the Go module**
    ``` $go mod init github.com/akhil/gql-yt
    ```

3. **Install gqlgen**
    ```
    $ go get github.com/99designs/gqlgen

    ```

4. **Add gqlgen to tools.go**
    ```
    $ printf '// +build tools\npackage tools\nimport _ "github.com/99designs/gqlgen"' | gofmt > tools.go

    ```

5. **Download dependencies**
    ```go mod tidy
    ```

6. **Initialize gqlgen**

    ```
    $ go run github.com/99designs/gqlgen init
    ```

7. **After writing your GraphQL schema, generate the necessary files**

    ```
    go run github.com/99designs/gqlgen generate
    ```
# 📌 GraphQL Operations

## 📍 Get All Jobs

    query GetAllJobs {
        jobs {
            _id
            title
            description
            company
            url
        }
    }

## 📍Create Job

    mutation CreateJobListing($input: CreateJobListingInput!) {
    createJobListing(input: $input) {
        _id
        title
        description
        company
        url
    }
}
### Variables:

{
  "input": {
    "title": "Software Development Engineer - I",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt",
    "company": "Google",
    "url": "www.google.com/"
  }
}

## 📍 Get Job by ID

query GetJob($id: ID!) {
  job(id: $id) {
    _id
    title
    description
    company
    url
  }
}
###  Variables:

{
  "id": "638051d7acc418c13197fdf7"
}


## 📍 Update Job by ID

mutation UpdateJob($id: ID!, $input: UpdateJobListingInput!) {
  updateJobListing(id: $id, input: $input) {
    _id
    title
    description
    company
    url
  }
}
### Variables:

{
  "id": "638051d3acc418c13197fdf6",
  "input": {
    "title": "Software Development Engineer - III"
  }
}
## 📍 Delete Job by ID

mutation DeleteQuery($id: ID!) {
  deleteJobListing(id: $id) {
    deletedJobId
  }
}
### Variables:

{
  "id": "638051d3acc418c13197fdf6"
}


