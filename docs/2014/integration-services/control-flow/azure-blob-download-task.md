---
title: Azure BLOB のダウンロード タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d6825d61a997969691405f312eb91afd8b514087
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287678"
---
# <a name="azure-blob-download-task"></a>Azure BLOB のダウンロード タスク
  Azure BLOB のダウンロード タスクを使うと、SSIS パッケージで Azure BLOB ストレージからファイルをダウンロードできます。   
**Azure BLOB のダウンロード タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックすると、次の **[Azure BLOB ダウンロード タスク エディター]** ダイアログ ボックスが表示されます。  
  
 次の表で、このダイアログ ボックスの各フィールドを説明します。  
  
|||  
|-|-|  
|**フィールド**|**[説明]**|  
|AzureStorageConnection|既存の Azure ストレージ接続マネージャーを指定するか、Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。この接続マネージャーは、BLOB ファイルがホストされている場所をポイントします。|  
|BlobContainer|ダウンロードする BLOB ファイルを含む BLOB コンテナーの名前を指定します。|  
|BlobDirectory|ダウンロードする BLOB ファイルを含む BLOB ディレクトリを指定します。 BLOB ディレクトリは仮想階層構造です。|  
|LocalDirectory|ダウンロードした BLOB ファイルが格納されるローカル ディレクトリを指定します。|  
|FileName|指定した名前のパターンを持つファイルを選択するための名前フィルターを指定します。 例: MySheet*.xls\* には、MySheet001.xls や MySheetABC.xlsx などのファイルが含まれます。|  
|TimeRangeFrom/TimeRangeTo|時間範囲フィルターを指定します。 **TimeRangeFrom** から **TimeRangeTo** までの間に変更されたファイルが含まれます。|  
  
  
