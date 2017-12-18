---
title: "Azure BLOB のアップロード タスク | Microsoft Docs"
ms.custom: 
ms.date: 07/25/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpblobuptask.f1
- sql14.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f71aed6c27291eaa7c9db171bcf55789b09f2867
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="azure-blob-upload-task"></a>Azure BLOB のアップロード タスク
**Azure BLOB のアップロード タスク** を使うと、SSIS パッケージで Azure BLOB ストレージにファイルをアップロードできます。
    
**Azure BLOB のアップロード タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックし、次の **[Azure Blob Upload Task Editor (Azure BLOB アップロード タスク エディター)]** ダイアログ ボックスを表示します。  
  
 **Azure BLOB のアップロード タスク**は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。
  
 次の表で、このダイアログ ボックスの各フィールドを説明します。  
  
|||  
|-|-|  
|**フィールド**|**Description**|  
|AzureStorageConnection|既存の Azure ストレージ接続マネージャーを指定するか、Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。この接続マネージャーは、BLOB ファイルがホストされている場所をポイントします。|  
|BlobContainer|アップロードしたファイルを BLOB として含む BLOB コンテナーの名前を指定します。|  
|BlobDirectory|アップロードしたファイルがブロック BLOB として格納される BLOB ディレクトリを指定します。 BLOB ディレクトリは仮想階層構造です。 BLOB が既に存在する場合は置き換えられます。|  
|LocalDirectory|アップロードするファイルを含むローカル ディレクトリを指定します。|  
|FileName|指定した名前のパターンを持つファイルを選択するための名前フィルターを指定します。 たとえば、`MySheet*.xls\*` には `MySheet001.xls` や `MySheetABC.xlsx` などのファイルが含まれます。|  
|TimeRangeFrom/TimeRangeTo|時間範囲フィルターを指定します。 **TimeRangeFrom** から **TimeRangeTo** までの間に変更されたファイルが含まれます。|  
  
  
