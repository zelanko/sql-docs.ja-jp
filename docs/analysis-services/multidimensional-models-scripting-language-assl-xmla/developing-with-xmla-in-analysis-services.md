---
title: Analysis Services の XMLA による開発 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc66eda3c4c81801fb2f008d83467ed03864dcab
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="developing-with-xmla-in-analysis-services"></a>Analysis Services での XMLA による開発
  XML for Analysis (XMLA) は SOAP ベースの XML プロトコルで、HTTP 接続を使用してアクセスできるあらゆる標準的な多次元データ ソースへの汎用データ アクセスを提供することを目的に特別に設計されています。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、クライアント アプリケーションとの通信を行う場合に、XMLA を唯一のプロトコルとして使用します。 基本的に、Analysis Services によってサポートされるすべてのクライアント ライブラリでは、要求と応答は XMLA で作成されます。  
  
 開発者は、.NET Framework または COM インターフェイスに依存しないで、XMLA を使用してクライアント アプリケーションと [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を統合できます。 広範なプラットフォームでのホスティングを含むアプリケーションの要件は、XMLA および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] への HTTP 接続を使用して満たすことができます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は XMLA の 1.1 仕様に完全に準拠していますが、データ定義、データ操作、データ制御のサポートを有効にするように拡張することもできます。 Analysis Services の拡張機能は、Analysis Services Scripting Language (ASSL) と呼ばれます。 XMLA と ASSL を組み合わせて使用すると、XMLA 単独より広範な機能セットを提供できます。 ASSL の詳細については、次を参照してください。 [Analysis Services スクリプト言語を使用した開発&#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[接続およびセッション管理&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに接続する方法、および XMLA でのセッションと状態保持を管理する方法について説明します。|  
|[エラーおよび警告の処理&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/handling-errors-and-warnings-xmla.md)|XMLA のメソッドやコマンドに関して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がどのようにエラーおよび警告情報を返すかについて説明します。|  
|[定義するオブジェクトを識別したり&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)|オブジェクト識別子とオブジェクト参照について、および XMLA コマンド内で識別子や参照を使用する方法について説明します。|  
|[トランザクションを管理する&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-transactions-xmla.md)|使用する方法の詳細、 [BeginTransaction](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)、 [CommitTransaction](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)、および[RollbackTransaction](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)を明示的に定義し、現在の XMLA でのトランザクション管理コマンドセッションです。|  
|[コマンドのキャンセル&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|使用する方法について説明します、[キャンセル](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)コマンド、セッション、および XMLA での接続をキャンセルするコマンド。|  
|[バッチ操作の実行&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md)|使用する方法について説明します、[バッチ](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)コマンドを複数の XMLA を実行するコマンドを直列または並列、同じトランザクション内で、または単一の XMLA を使用して、別のトランザクションとして[Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。|  
|[作成して、オブジェクトの変更&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md)|使用する方法について説明します、[作成](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)、 [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)、および[削除](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)コマンド、と共に、Analysis Services スクリプト言語 (ASSL) 要素を定義するには、変更、または削除オブジェクトから、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。|  
|[ロックおよびロック解除データベース&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/locking-and-unlocking-databases-xmla.md)|使用する方法の詳細、[ロック](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)と[Unlock](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)ロックおよびロック解除するためのコマンド、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。|  
|[オブジェクトの処理 & #40 です。XMLA & #41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md)|使用する方法について説明します、[プロセス](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)プロセスにコマンド、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクト。|  
|[パーティションのマージ&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md)|使用する方法について説明します、 [MergePartitions](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)パーティションをマージするコマンドを[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。|  
|[集計のデザイン&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)|使用する方法について説明します、 [DesignAggregations](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)反復のいずれかのコマンドをバッチ モードでの集計デザインの集計をデザインする[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。|  
|[バックアップ、復元、およびデータベースとその &#40; の同期XMLA と &#41; です。](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)|使用する方法について説明します、[バックアップ](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)と[復元](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)をバックアップおよび復元するためのコマンド、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース バックアップ ファイルからです。<br /><br /> 使用する方法についても説明、[同期](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)を同期するコマンド、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]同じインスタンスまたは別のインスタンスで既存のデータベースでのデータベースです。|  
|[挿入、更新、およびメンバーの削除&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)|使用する方法について説明します、[挿入](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[更新](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)、および[ドロップ](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)コマンドを追加するには、変更、またはメンバーを書き込み許可ディメンションから削除します。|  
|[セルの更新&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md)|使用する方法について説明します、 [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)書き込み許可パーティション内のセルの値を変更するコマンド。|  
|[キャッシュの管理&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-caches-xmla.md)|使用する方法の詳細、 [ClearCache](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)のキャッシュを消去するコマンド[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクト。|  
|[トレースの監視&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/monitoring-traces-xmla.md)|使用する方法について説明します、[購読](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)にサブスクライブし、既存のトレースを監視するコマンドを[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。|  
  
## <a name="data-mining-with-xmla"></a>XMLA を使用したデータ マイニング  
 XML for Analysis は、データ マイニング スキーマ行セットを完全にサポートしています。 これらの行セットを使用してデータ マイニング モデルのクエリについて説明します、 [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドです。 データ マイニング スキーマ行セットの詳細については、次を参照してください[データ マイニング スキーマ行セット。](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
 DMX の詳細については、次を参照してください。[データ マイニング拡張機能&#40;DMX&#41;参照](../../dmx/data-mining-extensions-dmx-reference.md)です。  
  
## <a name="namespace-and-schema"></a>名前空間とスキーマ  
  
### <a name="namespace"></a>名前空間  
 この仕様で定義されたスキーマが XML 名前空間を使用して`http://schemas.microsoft.com/AnalysisServices/2003/Engine`と標準的な省略形"DDL"  
  
### <a name="schema"></a>スキーマ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクト定義言語の XML Schema Definition Language (XSD) スキーマの定義は、このセクションのスキーマ要素および階層の定義に基づいています。  
  
## <a name="extensibility"></a>機能拡張  
 により、オブジェクト定義言語スキーマの拡張機能が提供される、**注釈**要素のすべてのオブジェクトに含まれています。 この要素には、次のルールに従って、XML 名前空間 (DDL を定義する対象の名前空間以外) の有効な XML を使用できます。  
  
-   XML には要素のみを使用できます。  
  
-   すべての要素に一意な名前を付ける必要があります。 お勧めの値**名前**ターゲット名前空間を参照します。  
  
 これらの規則が適用されるようにの内容、**注釈**タグは、Decision Support オブジェクト (DSO) 9.0 を介しての名前/値ペアのセットとして公開することができます。  
  
 コメントおよび内の空白、**注釈**子要素で囲まれていないタグが保存されない可能性があります。 また、すべての要素は読み取り書き込み要素である必要があり、読み取り専用の要素は無視されます。  
  
 スキーマで定義された要素の派生型の代替が許可されていないサーバーでは、オブジェクト定義言語スキーマは閉じられます。 このため、サーバーは、ここで定義された要素のセットのみを受け入れ、他の要素や属性は受け入れません。 不明な要素を使用すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エンジンにエラーが発生します。  
  
## <a name="see-also"></a>参照  
 [Services スクリプト言語の分析の使用による開発&#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Microsoft OLAP アーキテクチャについて](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
