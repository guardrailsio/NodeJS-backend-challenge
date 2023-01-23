# Node.js Engineer Coding Challenge

> This repository contains the coding challenge for backend engineers.

**Note:** Please don't fork this repository, create a pull request against it, or use GuardRails in the repo name. Otherwise other candidates may take inspiration from it. Once the coding challenge is completed, you can submit it via this [Google form](https://forms.gle/i5nZWZKoUnTWj3td9).

## Description

Simulate a code scanning application that detects vulnerabilities in git repository.
The application must fulfil the following requirements:
- A user can trigger a scan event (POST)
- A user can view a scan result (GET)

How to do a scan:
- When a scan is triggered, there should be a worker listening and acknowledging the message.
- When the worker is being invoked:
  - Sleep X (1 - 10) seconds after pick up an scan event
  - Generate randomly number of vulnerabilities (0 - 5) 
  - Based on the vulnerabilities, using this [free API](https://names.drycodes.com/20?nameOptions=funnyWords) to get randomly names representing for the file's name contains that one

The Entity should be stored in a database of your choice and have at least the following properties: 
- Result
  - A unique ID
  - A Scan ID foreign key
  - The findings, see the following example
    ```json
    {
      "findings": [
        {
          "type": "sast",
          "location": {
            "path": <random name goes here>,
            "positions": {
              "begin": {
                "line": <random int>
              }
            }
          }
        },
        {
          "type": "sast",
          "location": {
            "path": <random name goes here>,
            "positions": {
              "begin": {
                "line": <random int>
              }
            }
          }
        }
      ]
    }
    ```
- Scan Event
  - A unique ID
  - The repsository name
  - The scan's status (one of "Queued" | "In Progress" | "Success" - 0 vulnerability | "Failure" - 1+ vulnerability)
  - Timestamps that indicate when a scan was queued, as well as when the scan started and finished

**What we want to see:**
- Project Structure: Clear organization and structure of folders, code and functionality
- Idiomatic Code: Following established community standards, code consistency, use of linters, formatting, error handling, and anything else that shows your skills. Simple is better than complex
- Stack Knowledge: Proper use of Node.js (TypeScript) and selected frameworks / libraries with message queue
- Implementation: The implementation has to work according to the specs
- Unit Tests: Covering the core functionality with unit tests
- Proper Documentation: 
    - A High-Level Design for the components / infrastructure if any
    - Describe how you came up with the solution and what makes it a good one for the use-case
    - Describe how to configure the project, how to start it, how to test it etc
- SQL schema: proper modeling all entities and their relationship on the DB level

**Bonus points for:**

- Documentation
- Use of appropriate design patterns
- Code comments

**Things you don't have to worry about:**

- Authentication / Authorization
- CI configuration / Deployment
- APM


## Scoring

| General                | Points |
|------------------------|--------|
| Project structure      | 0-3    |
| Idiomatic code         | 0-3    |
| Stack Knowledge        | 0-3    |
| Implementation         | 0-3    |
| Unit tests             | 0-3    |
| README & Documentation | 0-3    |
| SQL Schema             | 0/1    | 

| Bonus             | Points |
|-------------------|--------|
| Code Comments     | 0/1    | 
| Dockerization     | 0/1    | 
| Design Patterns   | 0/1    | 

Maxium points: 22
