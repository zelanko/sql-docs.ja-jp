---
title: Azure Data Lake Store Source | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
author: yualan
ms.author: janinez
ms.openlocfilehash: 6e78c2533367ab45a31e926e02a0db115bb246f4
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925360"
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
