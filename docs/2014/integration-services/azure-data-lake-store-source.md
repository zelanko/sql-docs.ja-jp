---
title: Azure Data Lake Store Source | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
caps.latest.revision: 6
author: yualan
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5a09d4d1f62fdb862baf1bd44c72b371ec74eb15
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252664"
---
# <a name="azure-data-lake-store-source"></a>Azure Data Lake Store Source
  **Azure Data Lake Store Source** コンポーネントは、SSIS パッケージが Azure Data Lake Store からデータを読み取れるようにします。 サポートされるファイル形式は、テキストと Avro です。
  
## <a name="configure-the-azure-data-lake-store-source"></a>Azure Data Lake Store Source を構成する 
  
1.  Azure Data Lake Store のエディターを表示するには、データ フロー デザイナー上に **Azure Data Lake Store Source** をドラッグ アンド ドロップし、これをダブルクリックしてエディターを開きます。  
  
2.  **[Azure Data Lake Store connection manager (Azure Data Lake Store 接続マネージャー)]** フィールドに、既存の Azure Data Lake Store 接続マネージャーを指定するか、Azure Data Lake Store サービスを参照する新しいものを作成します。  
  
    1.  **[ファイル パス]** フィールドには、Azure Data Lake Store のソース ファイルのファイル パスを指定します。   
  
    2.  **[ファイル形式]** フィールドには、ソース ファイルのファイル形式を指定します。  
  
        テキスト ファイル形式の場合は、 **[列の区切り文字]** に値を指定する必要があります。 さらに、ファイルの 1 行目に列名が含まれている場合は、 **[先頭データ行を列名として使用する]** も指定する必要があります。  
  
3.  接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。  
