---
title: "Container support in Azure Cognitive Services"
titleSuffix: "Azure Cognitive Services"
description: Learn how Docker containers can get Cognitive Services closer to your data.
services: cognitive-services
author: diberry
manager: cgronlun

ms.service: cognitive-services
ms.topic: article 
ms.date: 12/04/2018
ms.author: diberry
#As a potential customer, I want to know more about how Cognitive Services provides and supports Docker containers for each service.
---

# Container support in Azure Cognitive Services

Container support in Azure Cognitive Services allows developers to use the same rich APIs that are available in Azure, and enables flexibility in where to deploy and host the services that come with [Docker containers](https://www.docker.com/what-container). Container support is currently available in preview for a subset of Azure Cognitive Services, including parts of [Computer Vision](Computer-vision/Home.md), [Face](Face/Overview.md), [Text Analytics](text-analytics/overview.md), and [Language Understanding](LUIS/luis-container-howto.md) (LUIS) .

Containerization is an approach to software distribution in which an application or service, including its dependencies & configuration, is packaged together as a container image. With little or no modification, a container image can be deployed on a container host. Containers are isolated from each other and the underlying operating system, with a smaller footprint than a virtual machine. Containers can be instantiated from container images for short-term tasks, and removed when no longer needed.

The following video demonstrates using a Cognitive Services container.

[![Container demonstration for Cognitive Services](./media/index/containers-video-image.png)](https://azure.microsoft.com/resources/videos/containers-support-of-cognitive-services)

The [Computer Vision](Computer-vision/Home.md), [Face](Face/Overview.md), [Text Analytics](text-analytics/overview.md), and [Language Understanding (LUIS)](LUIS/what-is-luis.md) services are available on [Microsoft Azure](https://azure.microsoft.com). Sign into the [Azure portal](https://portal.azure.com/) to create and explore Azure resources for these services.

## Features and benefits

- **Control over data**: Allow customers to choose where these Cognitive Services process their data.  This is essential for customers that cannot send data to the cloud but need access to Cognitive Services technology. Support consistency in hybrid environments  – across data, management, identity, and security.
- **Control over model updates**: Provide customers flexibility in versioning and updating of models deployed in their solutions.
- **Portable architecture**: Enable the creation of a portable application architecture that can be deployed in the cloud, on-premises and the edge. Containers can be deployed directly to [Azure Kubernetes Service](/azure/aks/), [Azure Container Instances](/azure/container-instances/), or to a [Kubernetes](https://kubernetes.io/) cluster deployed to [Azure Stack](/azure/azure-stack/). For more information, see [Deploy Kubernetes to Azure Stack](/azure/azure-stack/user/azure-stack-solution-template-kubernetes-deploy).
- **High throughput / low latency**: Provide customers the ability to scale for high throughput and low latency requirements by enabling Cognitive Services to run physically close to their application logic and data. Containers do not cap transactions per second (TPS) and can be made to scale both up and out to handle demand if you provide the necessary hardware resources. 


## Containers in Azure Cognitive Services

Azure Cognitive Services containers provide the following set of Docker containers, each of which contains a subset of functionality from services in Azure Cognitive Services:

| Service | Container| Description |
|---------|----------|-------------|
|[Computer Vision](Computer-vision/computer-vision-how-to-install-containers.md) |**Recognize Text** |Extracts printed text from images of various objects with different surfaces and backgrounds, such as receipts, posters, and business cards.<br/><br/>**Important:** The Recognize Text container currently works only with English.<br>[Request access](Computer-vision/computer-vision-how-to-install-containers.md#request-access-to-the-private-container-registry)|
|[Face](Face/face-how-to-install-containers.md) |**Face** |Detects human faces in images, and identifies attributes, including face landmarks (such as noses and eyes), gender, age, and other machine-predicted facial features. In addition to detection, Face can check if two faces in the same image or different images are the same by using a confidence score, or compare faces against a database to see if a similar-looking or identical face already exists. It can also organize similar faces into groups, using shared visual traits.<br>[Request access](Face/face-how-to-install-containers.md#request-access-to-the-private-container-registry) |
|[LUIS](LUIS/luis-container-howto.md) |**LUIS** ([image](https://go.microsoft.com/fwlink/?linkid=2043204))|Loads a trained or published Language Understanding model, also known as a LUIS app, into a docker container and provides access to the query predictions from the container's API endpoints. You can collect query logs from the container and upload these back to the [LUIS portal](https://www.luis.ai) to improve the app's prediction accuracy.|
|[Text Analytics](text-analytics/how-tos/text-analytics-how-to-install-containers.md) |**Key Phrase Extraction** ([image](https://go.microsoft.com/fwlink/?linkid=2018757)) |Extracts key phrases to identify the main points. For example, for the input text "The food was delicious and there were wonderful staff", the API returns the main talking points: "food" and "wonderful staff". |
|[Text Analytics](text-analytics/how-tos/text-analytics-how-to-install-containers.md)|**Language Detection** ([image](https://go.microsoft.com/fwlink/?linkid=2018759)) |For up to 120 languages, detects which language the input text is written in and report a single language code for every document submitted on the request. The language code is paired with a score indicating the strength of the score. |
|[Text Analytics](text-analytics/how-tos/text-analytics-how-to-install-containers.md)|**Sentiment Analysis** ([image](https://go.microsoft.com/fwlink/?linkid=2018654)) |Analyzes raw text for clues about positive or negative sentiment. This API returns a sentiment score between 0 and 1 for each document, where 1 is the most positive. The analysis models are pre-trained using an extensive body of text and natural language technologies from Microsoft. For [selected languages](https://docs.microsoft.com/azure/cognitive-services/text-analytics/text-analytics-supported-languages.md), the API can analyze and score any raw text that you provide, directly returning results to the calling application. |

## Container availability in Azure Cognitive Services

Azure Cognitive Services containers are publicly available through your Azure subscription, and Docker container images can be pulled from either the Microsoft Container Registry or Docker Hub. You can use the [docker pull](https://docs.docker.com/engine/reference/commandline/pull/) command to download a container image from the appropriate registry.

> [!IMPORTANT]
> Currently, you must complete a sign-up process to access the [Face](Face/face-how-to-install-containers.md) and [Recognize Text](Computer-vision/computer-vision-how-to-install-containers.md) containers, in which you fill out and submit a questionnaire with questions about you, your company, and the use case for which you want to implement the containers. Once you're granted access and provided credentials, you can then pull the container images for the Face and Recognize Text containers from a private container registry hosted by Azure Container Registry.

## Prerequisites

You must satisfy the following prerequisites before using Azure Cognitive Services containers:

**Docker Engine**: You must have Docker Engine installed locally. Docker provides packages that configure the Docker environment on [macOS](https://docs.docker.com/docker-for-mac/), [Linux](https://docs.docker.com/engine/installation/#supported-platforms), and [Windows](https://docs.docker.com/docker-for-windows/). On Windows, Docker must be configured to support Linux containers. Docker containers can also be deployed directly to [Azure Kubernetes Service](/azure/aks/) or [Azure Container Instances](/azure/container-instances/).

Docker must be configured to allow the containers to connect with and send billing data to Azure.

**Familiarity with Microsoft Container Registry and Docker**: You should have a basic understanding of both Microsoft Container Registry and Docker concepts, like registries, repositories, containers, and container images, as well as knowledge of basic `docker` commands.  

For a primer on Docker and container basics, see the [Docker overview](https://docs.docker.com/engine/docker-overview/).

Individual containers can have their own requirements, as well, including server and memory allocation requirements.

## Developer samples

Developer samples are available at our [Github repository](https://github.com/Azure-Samples/cognitive-services-containers-samples). 

## Next steps

Install and explore the functionality provided by containers in Azure Cognitive Services:

* [Install and use Computer Vision containers](Computer-vision/computer-vision-how-to-install-containers.md)
* [Install and use Face containers](Face/face-how-to-install-containers.md)
* [Install and use Text Analytics containers](text-analytics/how-tos/text-analytics-how-to-install-containers.md)
* [Install and use Language Understanding (LUIS) containers](LUIS/luis-container-howto.md)
