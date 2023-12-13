# model-deployment-scenarios


### Table 1: Perspectives on Training Application vs. Generative AI Application

| Aspect                       | Training Application                                                                                          | Generative AI Application                                                                 |
|------------------------------|--------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| **Model Development and Testing** | Involves creating, iterating, and validating AI models. Can occur in public cloud (Scenario 2) or locally (Scenario 3). | Not directly involved, as this phase precedes the generative AI application deployment.     |
| **Performance Lifecycle Management** | Continuous monitoring and updating of models to maintain performance. Relevant in both cloud and local scenarios. | Relies on well-maintained models for optimal performance but is not directly involved in this process. |
| **Drift Detection**          | Essential for ongoing model maintenance to ensure model accuracy over time.                                   | Depends on the training application to detect and correct drift for sustained accuracy in inference. |

### Table 2: Locality of Operations in AI Deployment Scenarios

| Scenario                     | Description                                                                                                   | Locality                                                                                                                                                        |
|------------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Scenario 1**               | Local Serving with Local Inference                                                                            | Entire process occurs on customer's premises. Offers high data privacy and low latency.                                                                         |
| **Scenario 2**               | Training in Public Cloud with Foundational Model                                                              | Training occurs in the public cloud, leveraging cloud resources for model development and iteration.                                                           |
| **Scenario 3**               | Local Training and Serving                                                                                    | Similar to Scenario 2, but all activities, including training and serving, happen locally at the customer's premises.                                           |
| **Scenario 4**               | Serving in Public Cloud with Local Inference                                                                  | AI model is served from the public cloud, but inference occurs locally at the customer's premises. Balances cloud capabilities with local data processing. |

graph TD
    subgraph Scenario 1 [Scenario 1: Local Serving with Local Inference]
        S1_Training[Training: Not Specified]
        S1_Serving[Serving: Local]
        S1_Inference[Inference: Local]
        S1_Data[Data Location: Local]
        S1_Training --> S1_Serving
        S1_Serving --> S1_Inference
        S1_Inference --> S1_Data
    end

    subgraph Scenario 2 [Scenario 2: Training in Public Cloud with Foundational Model]
        S2_Training[Training: Public Cloud]
        S2_Serving[Serving: Not Specified]
        S2_Inference[Inference: Not Specified]
        S2_Data[Data Location: Public Cloud]
        S2_Training --> S2_Serving
        S2_Serving --> S2_Inference
        S2_Inference --> S2_Data
    end

    subgraph Scenario 3 [Scenario 3: Local Training and Serving]
        S3_Training[Training: Local]
        S3_Serving[Serving: Local]
        S3_Inference[Inference: Local]
        S3_Data[Data Location: Local]
        S3_Training --> S3_Serving
        S3_Serving --> S3_Inference
        S3_Inference --> S3_Data
    end

    subgraph Scenario 4 [Scenario 4: Serving in Public Cloud with Local Inference]
        S4_Training[Training: Not Specified]
        S4_Serving[Serving: Public Cloud]
        S4_Inference[Inference: Local]
        S4_Data[Data Location: Exchanged between Public Cloud and Local]
        S4_Training --> S4_Serving
        S4_Serving --> S4_Inference
        S4_Inference --> S4_Data
    end
