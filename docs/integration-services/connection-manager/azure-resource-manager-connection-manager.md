---
title: "Azure リソース マネージャーの接続マネージャー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dd1dbf668bf3ac24d9d6598b0ff9e2256d897c42
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="azure-resource-manager-connection-manager"></a>Azure リソース マネージャーの接続マネージャー
**Azure リソース マネージャーの接続マネージャー** 、SSIS パッケージを使用して Azure リソースを管理するように、[サービス プリンシパル](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal)です。

**Azure リソース マネージャーの接続マネージャー**のコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。

作成および構成、 **Azure リソース マネージャーの接続マネージャー**、以下の手順に従います。

1. **SSIS 接続マネージャーの追加**ダイアログ ボックスで、 **AzureResourceManager**、 をクリック**追加**です。
2. **Azure リソース マネージャーの接続マネージャー エディター**  ダイアログ ボックスで、指定、**アプリケーション ID**、**アプリケーション キー**、および**テナント ID**サービス プリンシパルのです。 これらのプロパティの詳細についてを参照してください[この](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal)資料です。
3. **[OK]** をクリックして、ダイアログ ボックスを閉じます。
4. 作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。

