---
title: "Azure BLOB のアップロード タスク | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpblobuptask.f1"
  - "sql14.dts.designer.afpblobuptask.f1"
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# Azure BLOB のアップロード タスク
  **Azure BLOB のアップロード タスク**を使うと、SSIS パッケージで Azure BLOB ストレージにファイルをアップロードできます。
  
>   [!NOTE] Azure Storage 接続マネージャーとこれを使用するコンポーネント (つまり、Blob Source、Blob Destination、BLOB のアップロード タスク、および BLOB のダウンロード タスク) が汎用ストレージ アカウントと BLOB ストレージ アカウントの両方に接続できるようにするために、必ず最新バージョンの Azure Feature Pack を[こちら](https://www.microsoft.com/download/details.aspx?id=49492)からダウンロードしてください。 これら 2 種類のストレージ アカウントの詳細については、「[Microsoft Azure Storage の概要](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts)」を参照してください。 
    
**Azure BLOB のアップロード タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、**[編集]** をクリックし、次の **[Azure Blob Upload Task Editor (Azure BLOB アップロード タスク エディター)]** ダイアログ ボックスを表示します。  
  
 **Azure BLOB のアップロード タスク**は、SQL Server 2016 用の SQL Server Integration Services (SSIS) Feature Pack for Azure のコンポーネントです。 Feature Pack は [こちら](http://go.microsoft.com/fwlink/?LinkID=626967)からダウンロードしてください。  
  
 次の表で、このダイアログ ボックスの各フィールドを説明します。  
  
|||  
|-|-|  
|**フィールド**|**Description**|  
|AzureStorageConnection|既存の Azure ストレージ接続マネージャーを指定するか、Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。この接続マネージャーは、BLOB ファイルがホストされている場所をポイントします。|  
|BlobContainer|アップロードしたファイルを BLOB として保持する BLOB コンテナーの名前を指定します。|  
|BlobDirectory|アップロードしたファイルをブロック BLOB として格納する BLOB ディレクトリを指定します。 BLOB ディレクトリは仮想階層構造です。 BLOB が既に存在する場合は置き換えられます。|  
|LocalDirectory|アップロードするファイルを含むローカル ディレクトリを指定します。|  
|FileName|指定した名前のパターンを持つファイルを選択するための名前フィルターを指定します。 例:  MySheet*.xls\* には、MySheet001.xls や MySheetABC.xlsx などのファイルが含まれます。|  
|TimeRangeFrom/TimeRangeTo|時間範囲フィルターを指定します。 **TimeRangeFrom** から **TimeRangeTo** までの間に変更されたファイルが含まれます。|  
  
  