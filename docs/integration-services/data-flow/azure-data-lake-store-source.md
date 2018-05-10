---
title: Azure Data Lake Store Source | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSSRC.F1
- sql14.dts.designer.afpadlssrc.f1
ms.assetid: f9c3311f-7316-48d6-bf10-d810e70b4304
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 79cd70c9d36ab317ebf93f81203a0b1b9d77d008
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="azure-data-lake-store-source"></a>Azure Data Lake Store Source
  **Azure Data Lake Store Source** コンポーネントは、SSIS パッケージが Azure Data Lake Store からデータを読み取れるようにします。 サポートされるファイル形式は、テキストと Avro です。
  
 **Azure Data Lake Store Source** は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。  
  
>   [!NOTE]
> Azure Data Lake Store 接続マネージャーとこれを使用するコンポーネント (つまり、Azure Data Lake Store Source と Azure Data Lake Store Destination) がサービスに接続できるようにするために、必ず最新バージョンの Azure Feature Pack を [こちら](https://www.microsoft.com/download/details.aspx?id=49492)からダウンロードしてください。 
  
## <a name="configure-the-azure-data-lake-store-source"></a>Azure Data Lake Store Source を構成する
 1. Azure Data Lake Store のエディターを表示するには、データ フロー デザイナー上に **Azure Data Lake Store Source** をドラッグ アンド ドロップし、これをダブルクリックしてエディターを開きます。  
  
2.  **[Azure Data Lake Store connection manager (Azure Data Lake Store 接続マネージャー)]** フィールドに、既存の Azure Data Lake Store 接続マネージャーを指定するか、Azure Data Lake Store サービスを参照する新しいものを作成します。  
  
    1.  **[ファイル パス]** フィールドには、Azure Data Lake Store のソース ファイルのファイル パスを指定します。   
  
    2.  **[ファイル形式]** フィールドには、ソース ファイルのファイル形式を指定します。  
  
        テキスト ファイル形式の場合は、 **[列の区切り文字]** に値を指定する必要があります。 さらに、ファイルの 1 行目に列名が含まれている場合は、 **[先頭データ行を列名として使用する]** も指定する必要があります。  
  
3.  接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。   
