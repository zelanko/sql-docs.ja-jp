---
title: Azure Data Lake Store Destination | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
caps.latest.revision: 5
author: yualan
ms.author: yual
manager: jhubbard
ms.openlocfilehash: a68c0299d45a8665d7fb7ad14c92c9a58638c232
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173773"
---
# <a name="azure-data-lake-store-destination"></a>Azure Data Lake Store Destination
  **Azure Data Lake Store Destination** コンポーネントは、SSIS パッケージが Azure Data Lake Store にデータを書き込めるようにします。 サポートされるファイル形式は、テキスト、Avro、および ORC です。 
  
## <a name="configure-the-azure-data-lake-store-destination"></a>Azure Data Lake Store Destination を構成する 

1. **Azure Data Lake Store Destination** をデータ フロー デザイナーにドラッグ アンド ドロップし、ダブルクリックしてエディターを表示します。  

2.  **[Azure Data Lake Store connection manager (Azure Data Lake Store 接続マネージャー)]** フィールドに、既存の Azure Data Lake Store 接続マネージャーを指定するか、Azure Data Lake Store サービスを参照する新しいものを作成します。  
  
    1.  **[ファイル パス]** フィールドには、データを書き込むファイルの名前を指定します。 このファイルが既に存在する場合、その内容は上書きされます。  
  
    2.  **[ファイル形式]** フィールドには、使用するファイル形式を指定します。  
  
        テキスト ファイル形式の場合は、 **[列の区切り文字]** に値を指定する必要があります。 さらに、ファイルの 1 行目に列名が含まれている場合は、 **[先頭データ行を列名として使用する]** も指定する必要があります。  

        ORC ファイル形式の場合は、対応するプラットフォームの JRE をインストールする必要があります。 
  
3.  接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。  