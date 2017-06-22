---
title: "Microsoft COM ベースの競合回避モジュール | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: a6637e4b-4e6b-40aa-bee6-39d98cc507c8
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b0389bb0387489b581aae3225fd1a02e7bc9d713
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="advanced-merge-replication-conflict---com-based-resolvers"></a>マージ レプリケーションの競合の詳細 - COM ベースの競合回避モジュール
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のすべての COM ベースの競合回避モジュールでは、更新の競合が処理され、指定した場所で挿入および削除の競合が処理されます。 すべての競合回避モジュールで列追跡処理が可能です。また、ほとんどのモジュールで行追跡処理を行うこともできます。 この競合回避モジュール、および他の COM ベースの競合回避モジュールで処理可能な競合の種類が宣言され、それ以外の競合に対してはマージ  エージェントで既定の競合回避モジュールが使用されます。  
  
 競合回避モジュールは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインストール処理中にインストールされます。 コンピューターに登録されているすべての競合回避モジュールを表示するには、 **sp_enumcustomresolvers** ストアド プロシージャを実行してください。 個別の結果セット内にある各競合回避モジュールの説明とグローバル一意識別子 (GUID) が表示されます。  
  
 競合回避モジュールを指定するには、「 [Specify a Merge Article Resolver](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)」を参照してください。  
  
 次の表は、特定の競合回避モジュールの属性を示しています。  
  
|名前|必要な入力|説明|コメント|  
|----------|--------------------|-----------------|--------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver|合計する列の名前。 **int**、 **smallint**、 **numeric**などの算術データ型である必要があります。|優先される競合データは優先度値によって決まります。 指定された列の値は、変換元の列の値と変換先の列の値を合計した値に設定されます。 1 つを NULL に設定した場合、他の列の値に設定されます。|更新の競合を対象とし、列追跡のみを行います。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Averaging Conflict Resolver|平均をとる列の名前。 **int**、 **smallint**、 **numeric**などの算術データ型である必要があります。|優先される競合データは優先度値によって決まります。 結果の列の値は、変換元の列の値と変換先の列の値の平均値に設定されます。 1 つを NULL に設定した場合、他の列の値に設定されます。|更新の競合を対象とし、列追跡のみを行います。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] DATETIME (Earlier Wins) Conflict Resolver|競合で優先されるデータを指定するのに使用する列の名前。 **datetime** 型である必要があります。|**datetime** 値で日付の古い列のデータが優先されます。 1 つを NULL に設定した場合、それ以外を格納する行が競合で優先されます。|更新の競合を対象とし、行および列追跡を行います。 列の値は直接比較され、タイム ゾーンが異なる場合、調整は実行されません。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] DATETIME (Later Wins) Conflict Resolver|競合で優先されるデータを指定するのに使用する列の名前。 **datetime** 型である必要があります。|**datetime** 値で日付の新しい列のデータが優先されます。 1 つを NULL に設定した場合、それ以外を格納する行が競合で優先されます。|更新の競合を対象とし、行および列追跡を行います。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Maximum Conflict Resolver|競合で優先されるデータを指定するのに使用する列の名前。 **int**、 **smallint**、 **numeric**などの算術データ型である必要があります。|数値の大きい列のデータが優先されます。 1 つを NULL に設定した場合、それ以外を格納する行が競合で優先されます。|行および列追跡を行います。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Minimum Conflict Resolver|競合で優先されるデータを指定するのに使用する列の名前。 **int**、 **smallint**、 **numeric**などの算術データ型である必要があります。|数値の小さい列のデータが優先されます。 1 つを NULL に設定した場合、それ以外を格納する行が競合で優先されます。|更新の競合を対象とし、行および列追跡を行います。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Merge Text Conflict Resolver|`@resolver_info = '[col1][===]'`などのテキスト列と区切り記号の名前。|優先される競合データは優先度値によって決まります。 競合しているテキスト列は、マージされた値に設定されます。この値は、一般的なプレフィックスの後にパブリッシャーからの一意の部分、区切り記号、最後にサブスクライバーからの一意の部分の順で構成されます。|更新の競合を対象とし、列追跡のみを行います。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscriber Always Wins Conflict Resolver|入力なし。|変換元か変換先かにかかわらず、サブスクライバーのデータが優先されます。|全種類の競合を対象とします。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Priority Column Resolver|競合で優先されるデータを指定するのに使用する列の名前。 **int**、 **smallint**、 **numeric**などの算術データ型である必要があります。|数値の大きい列のデータが優先されます。 1 つを NULL に設定した場合、それ以外を格納する行が競合で優先されます。|更新の競合を対象とし、行および列追跡を行います。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Upload Only Conflict Resolver|入力なし。|パブリッシャーにアップロードされた変更が許容されます。変更はサブスクライバーにはダウンロードされません。|全種類の競合を対象とします。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Download Only Conflict Resolver|入力なし。|パブリッシャーにアップロードされた変更は拒否されます。変更はサブスクライバーにダウンロードされます。|全種類の競合を対象とします。|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLServer ストアド プロシージャ競合回避モジュール|競合を処理するために競合回避モジュールが呼び出すストアド プロシージャの名前。|競合の回避は、指定したストアド プロシージャのロジックに依存します。|更新の競合を対象とします。 詳細については、「[Implement a Custom Conflict Resolver for a Merge Article](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)」 (マージ アーティクルのカスタム競合回避モジュールの実装) を参照してください。|  
  
## <a name="see-also"></a>参照  
 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [sp_enumcustomresolvers (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md)  
  
  
