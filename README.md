# Keycloak-Spring Boot Integration

This project demonstrates the integration of Keycloak with a Spring Boot application. It uses Keycloak for authentication and authorization, allowing secure access to the application's resources.

## Features

- Keycloak integration with Spring Boot
- JWT-based authentication
- Secure REST API endpoints
- Role-based access control

## Requirements

- Java 17
- Spring Boot 3.3.3
- Keycloak 11.0.3
- MySQL (optional, if not using H2 Database)

## Getting Started

### Prerequisites

Ensure you have the following installed:

- [Java 17](https://www.oracle.com/java/technologies/javase-jdk17-downloads.html)
- [Maven](https://maven.apache.org/install.html)
- [Keycloak](https://www.keycloak.org/downloads)

### Keycloak Configuration

1. Start your Keycloak server.
2. Create a new realm named `SpringBoot-keycloak`.
3. Create a new client with the following configuration:
   - Client ID: `springboot-keycloak-client`
   - Access Type: `confidential`
   - Valid Redirect URIs: `http://localhost:8081/*`
4. Create roles and users as needed ( in this example i have two roles admin and user).

### Application Configuration

Update the `application.yml` file with your Keycloak and application settings.

### Running the Application
Clone the repository:

`git clone https://github.com/your-username/keycloak-springboot-example.git`


`cd keycloak-springboot-example`

Build and run the application:

`mvn clean install`

`mvn spring-boot:run`

### Test avec Postman
Obtenez un jeton d'accès depuis Keycloak :


**URL** : `http://localhost:8080/realms/SpringBoot-keycloak/protocol/openid-connect/token`

**Méthode** : `POST`

**En-têtes** : Content-Type: application/x-www-form-urlencoded

**Corps** :

 - client_id=springboot-keycloak-client
 - username=votre-nom-utilisateur
 - password=votre-mot-de-passe
 - grant_type=password
 - client_secret=votre-secret-client

**Explication** : Cette requête POST permet d'obtenir un jeton JWT depuis Keycloak en utilisant les informations d'identification de l'utilisateur.
![Design sans titre](https://github.com/user-attachments/assets/8e78c727-a865-489e-95ce-01d0fb1a3f59)
Utilisez le jeton pour accéder aux points de terminaison sécurisés :

**URL** : `http://localhost:8180/votre-endpoint-securise`

**Méthode** : `GET`

**En-têtes** : Authorization: Bearer votre-jeton-d-acces

![Design sans titre](https://github.com/user-attachments/assets/530a1b62-7fec-4cd2-8f93-842d82574bbc)

**Explication** : Utilisez le jeton JWT obtenu pour authentifier les requêtes aux points de terminaison sécurisés de votre application.

![Capture d’écran (136)](https://github.com/user-attachments/assets/07f35a5e-29c8-485a-8c93-b325e8735cc0)



