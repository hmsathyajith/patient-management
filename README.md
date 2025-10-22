# This is a complete microservices project using Spring boot technologies. 

Finally this will deoply to a AWS server.
As the first step we will create the patient service. 
We have used intelij's built in Http Request feature to test the end point. 

### 22/10/25
#### Adding patient related REST endpoints with validations. 
I have used @Valid and @Validation for that. 
The difference between @Valid and @Validation would be as follows;

Both @Valid and @Validation triggers bean validation on the PatientRequestDTO

### @Valid --> from Jakarta Bean Validation (JSR 380)
    -Comes from: jakarta.validation.Valid (or older javax.validation.Valid)
    -It is part of the Java Bean Validation standard, not Spring-specific.
    -It activates all constraints (@NotNull, @Size, @Email, etc.) on the object.
    -It does not support validation groups.
### @Validation --> from Spring framework
    -Comes from: org.springframework.validation.annotation.Validated
    -It’s a Spring-specific extension of @Valid.
    -It also triggers JSR 380 validation, but supports validation groups - that’s the key difference.

### What is the usage of validation groups?
If we use the same PatientRequestDTO for both create and update, @NotBlank fields will fail validation 
during updates since only partial data (e.g., id and name) is sent. 
Validation groups solve this by defining marker interfaces (e.g., Create and Update) and 
applying them to DTO fields, allowing different validation rules for each operation.

The implementation of validation group is by just adding a interface and mark the DTO's property with that interface. 
That's it. 

### Adding Swagger
Added Swagger documentation tool to have web based API documentation. 
