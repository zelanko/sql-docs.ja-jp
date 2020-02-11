---
title: XML 入力ファイル リファレンス (データベース エンジン チューニング アドバイザー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b560b36eb98ec73723a4ce25cb3c647f4962b634
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62509984"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>XML 入力ファイル リファレンス (データベース エンジン チューニング アドバイザー)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)]チューニングアドバイザーでは、XML 入力ファイルを使用してデータベースをチューニングできます。 この XML ファイルでは、チューニング セッションで使用するデータベース、テーブル、ワークロード ファイルまたはワークロード テーブル、およびチューニング オプションを指定します。 このファイルを使用して、ユーザー指定の構成を指定し、"what-if" 分析を実行することもできます。  
  
 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML 入力ファイルには XML 要素の階層が含まれており、各要素には、チューニング セッションの設定を指定するテキスト、またはその他の要素が含まれています。 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML 入力ファイルは整形式 XML の標準に準拠する必要があるため、すべての要素名で大文字と小文字が区別されます。 要素の大文字と小文字の記述は Pascal 形式にします。つまり、最初の文字を大文字で表記し、結合されている後に続く単語の最初の文字も大文字で表記します。  
  
 すべての要素の値は、XML の名前付け規則に準拠している必要があります。 これらの規則の詳細については、MSDN ライブラリの「 [XML テキストの内容](https://go.microsoft.com/fwlink/?LinkId=7614) 」を参照してください。  
  
 このリファレンスは包括的なものではないことに注意してください。 XML 入力を定義するために使用できるすべての要素の詳細については、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML スキーマ DTASchema.xsd を参照してください。  
  
## <a name="xml-declaration"></a>XML 宣言  
  
-   [XML データ &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>DTAXML ルート要素  
  
-   [DTA&#41;&#40;DTAXML 要素](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>DTAInput 要素  
  
-   [DTAInput 要素 &#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [Server 要素 &#40;DTA&#41;](server-element-dta.md)  
  
-   [ワークロード要素 &#40;DTA&#41;](workload-element-dta.md)  
  
-   [TuningOptions 要素 &#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [DTA&#41;&#40;構成要素](configuration-element-dta.md)  
  
## <a name="server-elements"></a>サーバー要素  
  
-   [サーバー &#40;DTA&#41;の Name 要素](name-element-for-server-dta.md)  
  
-   [サーバー &#40;DTA&#41;の Database 要素](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Workload 要素  
  
-   [DTA&#41;&#40;File 要素](file-element-dta.md)  
  
-   [DTA&#41;&#40;ワークロードの Database 要素](database-element-for-workload-dta.md)  
  
-   [DTA&#41;&#40;EventString 要素](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>チューニング オプションの要素  
  
-   [TuningTimeInMin 要素 &#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [StorageBoundInMB 要素 &#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [TestServer 要素 &#40;DTA&#41;](testserver-element-dta.md)  
  
-   [FeatureSet 要素 &#40;DTA&#41;](featureset-element-dta.md)  
  
-   [DTA&#41;&#40;のパーティション分割要素](partitioning-element-dta.md)  
  
-   [DropOnlyMode 要素 &#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [KeepExisting 要素 &#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [&#40;DTA&#41;のオンラインインデックス操作要素](onlineindexoperation-element-dta.md)  
  
-   [DatabaseToConnect 要素 &#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>構成の要素  
  
-   [DTA&#41;の Configuration &#40;の Server 要素](server-element-for-configuration-dta.md)  
  
-   [DTA&#41;の Configuration &#40;の Database 要素](database-element-for-configuration-dta.md)  
  
-   [DTA&#41;&#40;推奨要素](recommendation-element-dta.md)  
  
-   [DTA&#41;&#40;要素の作成](create-element-dta.md)  
  
-   [DTA&#41;&#40;の Index 要素](index-element-dta.md)  
  
-   [&#40;DTA&#41;の Index の Name 要素](name-element-for-index-dta.md)  
  
-   [&#40;DTA&#41;の Index の Column 要素](column-element-for-index-dta.md)  
  
-   [DTA&#41;&#40;列の Name 要素](name-element-for-column-dta.md)  
  
-   [&#40;DTA&#41;の Index の Filegroup 要素](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>データベースの要素  
  
-   [Database の Name 要素 &#40;DTA&#41;](name-element-for-database-dta.md)  
  
-   [Database の Schema 要素 &#40;DTA&#41;](schema-element-for-database-dta.md)  
  
-   [スキーマ &#40;DTA&#41;の Name 要素](name-element-for-schema-dta.md)  
  
-   [スキーマ &#40;DTA&#41;の Table 要素](table-element-for-schema-dta.md)  
  
-   [Table &#40;DTA&#41;の Name 要素](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>参照  
 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
