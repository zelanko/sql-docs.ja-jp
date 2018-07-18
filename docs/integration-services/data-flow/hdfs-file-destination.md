---
title: HDFS ファイル変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 88b6bc5bafcc2fe3da77b55ac98d19ab7ec747e2
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35410704"
---
# <a name="hdfs-file-destination"></a>HDFS ファイル変換先
  HDFS ファイル変換先コンポーネントは、SSIS パッケージが HDFS ファイルにデータを書き込めるようにします。 サポートされるファイル形式は、テキスト、Avro、および ORC です。  
  
 HDFS ファイル変換先を構成するには、HDFS ファイル ソースをデータ フロー デザイナー上にドラッグ アンド ドロップし、このコンポーネントをダブルクリックしてエディターを開きます。  
  
 ![HDFS ファイル変換先エディター](../../integration-services/data-flow/media/hdfs-file-dest.png "HDFS ファイル変換先エディター")  
  
## <a name="options"></a>および  
 **[Hadoop File Destination Editor]** (Hadoop ファイル変換先エディター) ダイアログ ボックスの **[全般]** タブで、次のオプションを構成します。  
  
|フィールド|[説明]|  
|-----------|-----------------|  
|**Hadoop 接続**|既存の Hadoop 接続マネージャーを指定するか、新しい Hadoop 接続マネージャーを作成します。 この接続マネージャーは、HDFS ファイルがホストされる場所を示します。|  
|**ファイル パス**|HDFS ファイルの名前を指定します。|  
|**ファイル形式**|HDFS ファイルの形式を指定します。 テキスト、Avro、または ORC 形式を選択できます。|  
|**Column delimiter character (列区切り文字)**|テキスト形式を選択した場合は、列区切り文字を指定します。|  
|**先頭データ行を列名として使用する**|テキスト形式を選択した場合は、ファイルの最初の行に列の名前が含まれるかどうかを示します。|  
  
 これらのオプションを構成した後、 **[列]** タブを選択し、データ フローのソース列を変換先列にマップします。  
  
## <a name="see-also"></a>参照  
 [Hadoop 接続マネージャー](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [HDFS ファイル変換元](../../integration-services/data-flow/hdfs-file-source.md)  
  
  
