---
title: "パッケージの再配置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージの再配置 [Integration Services]"
  - "パッケージの配置 [Integration Services], 再配置"
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# パッケージの再配置
  プロジェクトの配置後に、パッケージの機能を更新または拡張し、更新したパッケージを含む [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを再配置する必要がある場合があります。 パッケージの再配置プロセスの一環として、配置ユーティリティに含まれている構成プロパティを見直す必要があります。 たとえば、パッケージの再配置後に構成が変更されないようにする場合などがあります。  
  
## 再配置のプロセス  
 パッケージの更新の終了後、プロジェクトを再構築し、配置先のコンピューターに配置フォルダーをコピーしてから、パッケージ インストール ウィザードを再度実行します。  
  
 プロジェクトのパッケージの一部だけを更新した場合、プロジェクト全体を再配置する必要がないことがあります。 パッケージの一部だけを配置するために、新しい [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを作成して、このプロジェクトに更新したパッケージを追加し、プロジェクトをビルドして配置できます。 パッケージの構成は、パッケージを別のプロジェクトに追加する際に、自動的にパッケージと共にコピーされます。  
  
## 関連タスク  
 [配置ユーティリティを使用してパッケージを配置する](../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md)  
  
  