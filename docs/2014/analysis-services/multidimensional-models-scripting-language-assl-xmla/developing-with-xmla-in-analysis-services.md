---
title: Analysis Services での XMLA による開発 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, data mining
- commands [XML for Analysis]
- data mining [XML for Analysis]
- XMLA, data mining
- XML for Analysis, Analysis Services tasks
- XMLA, Analysis Services tasks
ms.assetid: 54445ee7-720c-4683-99a6-e75b3dcca904
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2f5455b71306b3dd75406f107e5c1e971f6b923b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545004"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Analysis Services での XMLA による開発
  XML for Analysis (XMLA) は SOAP ベースの XML プロトコルで、HTTP 接続を使用してアクセスできるあらゆる標準的な多次元データ ソースへの汎用データ アクセスを提供することを目的に特別に設計されています。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、クライアント アプリケーションとの通信を行う場合に、XMLA を唯一のプロトコルとして使用します。 基本的に、Analysis Services によってサポートされるすべてのクライアント ライブラリでは、要求と応答は XMLA で作成されます。  
  
 開発者は、.NET Framework または COM インターフェイスに依存しないで、XMLA を使用してクライアント アプリケーションと [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を統合できます。 広範なプラットフォームでのホスティングを含むアプリケーションの要件は、XMLA および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] への HTTP 接続を使用して満たすことができます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は XMLA の 1.1 仕様に完全に準拠していますが、データ定義、データ操作、データ制御のサポートを有効にするように拡張することもできます。 Analysis Services の拡張機能は、Analysis Services Scripting Language (ASSL) と呼ばれます。 XMLA と ASSL を組み合わせて使用すると、XMLA 単独より広範な機能セットを提供できます。 ASSL の詳細については、「 [Analysis Services スクリプト言語 &#40;assl&#41;を使用した開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[接続およびセッションの管理 (XMLA)](managing-connections-and-sessions-xmla.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに接続する方法、および XMLA でのセッションと状態保持を管理する方法について説明します。|  
|[XMLA&#41;&#40;エラーと警告の処理](handling-errors-and-warnings-xmla.md)|XMLA のメソッドやコマンドに関して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がどのようにエラーおよび警告情報を返すかについて説明します。|  
|[XMLA&#41;&#40;のオブジェクトの定義と識別](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|オブジェクト識別子とオブジェクト参照について、および XMLA コマンド内で識別子や参照を使用する方法について説明します。|  
|[XMLA&#41;&#40;のトランザクションの管理](managing-transactions-xmla.md)|[BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla)、 [committransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)、および[RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla)コマンドを使用して、現在の XMLA セッションでトランザクションを明示的に定義および管理する方法について詳しく説明します。|  
|[XMLA&#41;&#40;コマンドを取り消す](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|[[キャンセル](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)] コマンドを使用して、XMLA のコマンド、セッション、および接続をキャンセルする方法について説明します。|  
|[XMLA&#41;&#40;のバッチ操作の実行](performing-batch-operations-xmla.md)|1つの XMLA [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドを使用して、[バッチ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)コマンドを使用して、同じトランザクション内または個別のトランザクション内で複数の xmla コマンドを直列または並列で実行する方法について説明します。|  
|[XMLA&#41;&#40;のオブジェクトの作成と変更](creating-and-altering-objects-xmla.md)|[Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)、 [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)、および[Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla)コマンドを Analysis Services スクリプト言語 (assl) 要素と共に使用して、インスタンスのオブジェクトを定義、変更、または削除する方法について説明し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。|  
|[XMLA&#41;&#40;データベースのロックとロック解除](locking-and-unlocking-databases-xmla.md)|[ロック](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)およびロック[解除](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)コマンドを使用してデータベースのロックとロック解除を行う方法について詳しく説明し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。|  
|[オブジェクトの処理 &#40;XMLA&#41;](processing-objects-xmla.md)|[Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)コマンドを使用してオブジェクトを処理する方法について説明し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。|  
|[XMLA&#41;&#40;のパーティションのマージ](merging-partitions-xmla.md)|[Mergepartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla)コマンドを使用して、インスタンス上のパーティションをマージする方法について説明し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。|  
|[XMLA&#41;&#40;の集計のデザイン](designing-aggregations-xmla.md)|では、 [designaggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla)コマンドを反復モードまたはバッチモードで使用して、の集計デザインの集計をデザインする方法について説明し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。|  
|[データベースのバックアップ、復元、および同期 &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|[Backup コマンド](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)と[restore](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)コマンドを使用して、バックアップファイルからデータベースをバックアップおよび復元する方法について説明し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。<br /><br /> また、 [synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)コマンドを使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 同じインスタンスまたは別のインスタンス上の既存のデータベースとデータベースを同期する方法についても説明します。|  
|[XMLA&#41;&#40;のメンバーの挿入、更新、および削除](inserting-updating-and-dropping-members-xmla.md)|[Insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)、 [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)、および[Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla)コマンドを使用して、書き込み許可ディメンションのメンバーを追加、変更、または削除する方法について説明します。|  
|[XMLA&#41;&#40;のセルの更新](updating-cells-xmla.md)|[UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla)コマンドを使用して、書き込み可能なパーティション内のセルの値を変更する方法について説明します。|  
|[XMLA&#41;&#40;キャッシュを管理する](managing-caches-xmla.md)|[Clearcache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla)コマンドを使用してオブジェクトのキャッシュを消去する方法について詳しく説明し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。|  
|[XMLA&#41;&#40;トレースの監視](monitoring-traces-xmla.md)|[Subscribe](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla)コマンドを使用して、インスタンス上の既存のトレースをサブスクライブおよび監視する方法について説明し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。|  
  
## <a name="data-mining-with-xmla"></a>XMLA を使用したデータ マイニング  
 XML for Analysis は、データ マイニング スキーマ行セットを完全にサポートしています。 これらの行セットは、 [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)メソッドを使用してデータマイニングモデルにクエリを実行するための情報を提供します。 データマイニングスキーマ行セットの詳細については、「[データマイニングスキーマ行](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets)セット」を参照してください。 
  
 DMX の詳細については、「[データマイニング拡張機能 &#40;dmx&#41; リファレンス](/sql/dmx/data-mining-extensions-dmx-reference)」を参照してください。  
  
## <a name="namespace-and-schema"></a>名前空間とスキーマ  
  
### <a name="namespace"></a>名前空間  
 この仕様で定義されているスキーマでは、XML 名前空間 `https://schemas.microsoft.com/AnalysisServices/2003/Engine` と標準の省略形 "DDL" を使用します。  
  
### <a name="schema"></a>スキーマ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクト定義言語の XML Schema Definition Language (XSD) スキーマの定義は、このセクションのスキーマ要素および階層の定義に基づいています。  
  
## <a name="extensibility"></a>機能拡張  
 オブジェクト定義言語スキーマの拡張性は、すべてのオブジェクトに含まれている `Annotation` 要素によって提供されます。 この要素には、次のルールに従って、XML 名前空間 (DDL を定義する対象の名前空間以外) の有効な XML を使用できます。  
  
-   XML には要素のみを使用できます。  
  
-   すべての要素に一意な名前を付ける必要があります。 `Name` の値が対象の名前空間を参照するように指定してください。  
  
 これらのルールは、`Annotation` タグの内容を名前/値ペアのセットとして Decision Support オブジェクト (DSO) 9.0 を介して公開するために設定されています。  
  
 子要素で囲まれていない `Annotation` タグ内のコメントおよび空白は保存されません。 また、すべての要素は読み取り書き込み要素である必要があり、読み取り専用の要素は無視されます。  
  
 スキーマで定義された要素の派生型の代替が許可されていないサーバーでは、オブジェクト定義言語スキーマは閉じられます。 このため、サーバーは、ここで定義された要素のセットのみを受け入れ、他の要素や属性は受け入れません。 不明な要素を使用すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エンジンにエラーが発生します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語 &#40;ASSL&#41;を使用した開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Microsoft OLAP アーキテクチャについて](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
