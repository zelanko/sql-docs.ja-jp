---
title: Azure Data Lake Store Destination | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: chugu
ms.openlocfilehash: 14248d14b6a944250c33a19c8cf83ab0e0330587
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439419"
---
# <a name="azure-data-lake-store-destination"></a>Azure Data Lake Store Destination
  **Azure Data Lake Store Destination** コンポーネントは、SSIS パッケージが Azure Data Lake Store にデータを書き込めるようにします。 サポートされるファイル形式は、テキスト、Avro、および ORC です。 
  
## <a name="configure-the-azure-data-lake-store-destination"></a>Azure Data Lake Store Destination を構成する 

1. **Azure Data Lake Store Destination** をデータ フロー デザイナーにドラッグ アンド ドロップし、ダブルクリックしてエディターを表示します。  

2.  **[Azure Data Lake Store connection manager (Azure Data Lake Store 接続マネージャー)]** フィールドに、既存の Azure Data Lake Store 接続マネージャーを指定するか、Azure Data Lake Store サービスを参照する新しいものを作成します。  
  
    1.  **[ファイル パス]** フィールドには、データを書き込むファイルの名前を指定します。 このファイルが既に存在する場合、その内容は上書きされます。  
  
    2.  **[ファイル形式]** フィールドには、使用するファイル形式を指定します。  
  
        テキスト ファイル形式の場合は、 **[列の区切り文字]** に値を指定する必要があります。 また、ファイルの最初の行に列名が含まれている場合は、**最初のデータ行で列名**を選択します。  

        ORC ファイル形式の場合は、対応するプラットフォームの JRE をインストールする必要があります。 
  
3.  接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。  
