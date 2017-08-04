---
title: "Azure Blob ダウンロード タスク |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/25/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpblobdltask.f1
- sql14.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 95ea7de4600551cc994e82dd3408cb4ea608685c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="azure-blob-download-task"></a>Azure BLOB のダウンロード タスク
Azure BLOB のダウンロード タスクを使うと、SSIS パッケージで Azure BLOB ストレージからファイルをダウンロードできます。

**Azure BLOB のダウンロード タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックすると、次の **[Azure BLOB ダウンロード タスク エディター]** ダイアログ ボックスが表示されます。  
  
 **Azure Blob ダウンロード タスク**のコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。  
  
 次の表で、このダイアログ ボックスの各フィールドを説明します。  
  
|||  
|-|-|  
|**フィールド**|**Description**|  
|AzureStorageConnection|既存の Azure ストレージ接続マネージャーを指定するか、Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。この接続マネージャーは、BLOB ファイルがホストされている場所をポイントします。|  
|BlobContainer|ダウンロードする BLOB ファイルを含む BLOB コンテナーの名前を指定します。|  
|BlobDirectory|ダウンロードする BLOB ファイルを含む BLOB ディレクトリを指定します。 BLOB ディレクトリは仮想階層構造です。|  
|LocalDirectory|ダウンロードした blob ファイルが格納されているローカル ディレクトリを指定します。|  
|FileName|指定した名前のパターンを持つファイルを選択するための名前フィルターを指定します。 たとえば、`MySheet*.xls\*`などのファイルが含まれる`MySheet001.xls`と`MySheetABC.xlsx`です。|  
|TimeRangeFrom/TimeRangeTo|時間範囲フィルターを指定します。 変更されたファイル**TimeRangeFrom**前に**TimeRangeTo**が含まれています。|  
  
  

