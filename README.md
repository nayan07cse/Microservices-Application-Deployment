# Microservices-Application-Deployment

This project demonstrates deploying a microservices-based application on IBM Cloud Code Engine. It includes two backend microservices (Python and Node.js) and a frontend microservice.

---

## Command Explanation

- **`ibmcloud ce application create`**  
  This command is used to deploy applications on IBM Cloud Code Engine. It creates an application with the specified name, image, port, and other parameters.

---

## Deployment Steps

### 1. Backend Microservices
- **Product Details Microservice**  
  Deploy command:  
  ```bash
  ibmcloud ce application create --name prodlist --image us.icr.io/${SN_ICR_NAMESPACE}/prodlist --registry-secret icr-secret --port 5000 --build-context-dir products_list --build-source https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git
  ```

- **Dealer Pricing Microservice**  
  Deploy command:  
  ```bash
  ibmcloud ce application create --name dealerdetails --image us.icr.io/${SN_ICR_NAMESPACE}/dealerdetails --registry-secret icr-secret --port 8080 --build-context-dir dealer_details --build-source https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git
  ```

---

### 2. Frontend Microservice
1. Clone the frontend repository:  
   ```bash
   git clone https://github.com/ibm-developer-skills-network/dealer_evaluation_frontend.git
   ```
2. Update `index.html` with backend microservice URLs.
3. Deploy the frontend:  
   ```bash
   ibmcloud ce application create --name frontend --image us.icr.io/${SN_ICR_NAMESPACE}/frontend --registry-secret icr-secret --port 5001 --build-source .
   ```

---

## Application URL
Access the application:  
`[https://frontend.<unique-id>.us-south.codeengine.appdomain.cloud/](https://frontend.26r0lkimyq12.us-south.codeengine.appdomain.cloud/)`

---

