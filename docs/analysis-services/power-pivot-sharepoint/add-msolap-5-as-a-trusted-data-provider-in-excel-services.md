---
title: "Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1f40fa4-de6d-41ee-8124-14b4d65988f5
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bbf52055cb77be6a740fc5186c69d55c352d5cc7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a>Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]MSOLAP.5 は、SQL Server 2012 Analysis Services OLE DB プロバイダーを参照します。 Excel Services は、サーバー上の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを利用可能とする接続要求を行う前に、このプロバイダーを信頼する必要があります。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint を構成した場合、このツールは要件を満たすアクションを含むため、MSOLAP.5 は、既に信頼されたプロバイダーとなっている可能性があります。 ただし、PowerShell や全体管理を使用している場合、または信頼されたプロバイダー アクションを構成ツールで除外している場合は、このプロバイダーが不足している可能性があります。その場合は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスのファームを構成するときに、それを追加する必要があります。  
  
 この手順は、各 Excel Services サービス アプリケーションにつき 1 回実行するだけです。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーまたは Excel Services サーバーなど、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ要求を処理する物理サーバーでは、コンピューターに OLE DB プロバイダーをインストールする必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint のインストールには常に OLE DB プロバイダーが含まれていますが、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がないコンピューターで Excel Services が実行されている場合は、プロバイダーを手動でインストールする必要があります。 「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859)」を参照してください。  
  
## <a name="add-a-trusted-provider-to-excel-services"></a>Excel Services に信頼できるプロバイダーを追加する  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]**をクリックし、Excel Services サービス アプリケーションをクリックします。  
  
2.  **[信頼できるデータ プロバイダー]**をクリックします。  
  
3.  MSOLAP.5 が一覧に表示されていることを確認します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint の構成方法によっては、MSOLAP.5 が既に信頼されている場合があります。  
  
4.  表示されない場合は、 **[信頼できるデータ プロバイダーの追加]**をクリックします。  
  
5.  [プロバイダー ID] に、「 **MSOLAP.5**」と入力します。  
  
6.  [プロバイダーの種類] では、OLE DB が選択されていることを確認します。  
  
7.  [プロバイダーの説明] に、「 **Microsoft OLE DB プロバイダー (OLAP Services 11.0 用)**」と入力します。  
  
  
