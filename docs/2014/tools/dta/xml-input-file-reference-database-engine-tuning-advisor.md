---
title: XML 入力ファイル リファレンス (データベース エンジン チューニング アドバイザー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7dd0170481a3894334dc01b2974a27ace6b736b4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073876"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>XML 入力ファイル リファレンス (データベース エンジン チューニング アドバイザー)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーでは、XML 入力ファイルを使用してデータベースをチューニングできます。 この XML ファイルでは、チューニング セッションで使用するデータベース、テーブル、ワークロード ファイルまたはワークロード テーブル、およびチューニング オプションを指定します。 このファイルを使用して、ユーザー指定の構成を指定し、"what-if" 分析を実行することもできます。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML 入力ファイルには XML 要素の階層が含まれており、各要素には、チューニング セッションの設定を指定するテキスト、またはその他の要素が含まれています。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML 入力ファイルは整形式 XML の標準に準拠する必要があるため、すべての要素名で大文字と小文字が区別されます。 要素の大文字と小文字の記述は Pascal 形式にします。つまり、最初の文字を大文字で表記し、結合されている後に続く単語の最初の文字も大文字で表記します。  
  
 すべての要素の値は、XML の名前付け規則に準拠している必要があります。 これらの規則の詳細については、MSDN ライブラリの「 [XML テキストの内容](http://go.microsoft.com/fwlink/?LinkId=7614) 」を参照してください。  
  
 このリファレンスは包括的なものではないことに注意してください。 XML 入力を定義するために使用できるすべての要素の詳細については、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML スキーマ DTASchema.xsd を参照してください。  
  
## <a name="xml-declaration"></a>XML 宣言  
  
-   [XML データ &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>DTAXML ルート要素  
  
-   [DTAXML 要素&#40;DTA&#41;](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>DTAInput 要素  
  
-   [DTAInput 要素&#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [サーバー要素&#40;DTA&#41;](server-element-dta.md)  
  
-   [Workload 要素&#40;DTA&#41;](workload-element-dta.md)  
  
-   [TuningOptions 要素&#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [構成要素&#40;DTA&#41;](configuration-element-dta.md)  
  
## <a name="server-elements"></a>サーバー要素  
  
-   [サーバーの名前を要素&#40;DTA&#41;](name-element-for-server-dta.md)  
  
-   [Server の database 要素&#40;DTA&#41;](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Workload 要素  
  
-   [要素が&#40;DTA&#41;](file-element-dta.md)  
  
-   [ワークロードの database 要素&#40;DTA&#41;](database-element-for-workload-dta.md)  
  
-   [EventString 要素&#40;DTA&#41;](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>チューニング オプションの要素  
  
-   [TuningTimeInMin 要素&#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [StorageBoundInMB 要素&#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [TestServer 要素&#40;DTA&#41;](testserver-element-dta.md)  
  
-   [FeatureSet 要素&#40;DTA&#41;](featureset-element-dta.md)  
  
-   [Partitioning 要素&#40;DTA&#41;](partitioning-element-dta.md)  
  
-   [DropOnlyMode 要素&#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [KeepExisting 要素&#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [OnlineIndexOperation 要素&#40;DTA&#41;](onlineindexoperation-element-dta.md)  
  
-   [DatabaseToConnect 要素&#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>構成の要素  
  
-   [Configuration の server 要素&#40;DTA&#41;](server-element-for-configuration-dta.md)  
  
-   [Configuration の database 要素&#40;DTA&#41;](database-element-for-configuration-dta.md)  
  
-   [Recommendation 要素&#40;DTA&#41;](recommendation-element-dta.md)  
  
-   [要素を作成する&#40;DTA&#41;](create-element-dta.md)  
  
-   [要素のインデックス&#40;DTA&#41;](index-element-dta.md)  
  
-   [インデックスの要素の名前を付けます&#40;DTA&#41;](name-element-for-index-dta.md)  
  
-   [Index の column 要素&#40;DTA&#41;](column-element-for-index-dta.md)  
  
-   [列の要素の名前を付けます&#40;DTA&#41;](name-element-for-column-dta.md)  
  
-   [Index の Filegroup 要素&#40;DTA&#41;](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>データベースの要素  
  
-   [データベースの要素の名前を付けます&#40;DTA&#41;](name-element-for-database-dta.md)  
  
-   [Database の schema 要素&#40;DTA&#41;](schema-element-for-database-dta.md)  
  
-   [スキーマの要素の名前を付けます&#40;DTA&#41;](name-element-for-schema-dta.md)  
  
-   [スキーマの要素をテーブル&#40;DTA&#41;](table-element-for-schema-dta.md)  
  
-   [テーブルの要素の名前を付けます&#40;DTA&#41;](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>参照  
 [データベース エンジン チューニング アドバイザー](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  