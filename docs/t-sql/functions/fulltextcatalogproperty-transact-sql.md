---
title: "FULLTEXTCATALOGPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FULLTEXTCATALOGPROPERTY_TSQL
- FULLTEXTCATALOGPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- full-text catalogs [SQL Server], properties
- FULLTEXTCATALOGPROPERTY function
- status information [SQL Server], full-text catalogs
ms.assetid: f841dc79-2044-4863-aff0-56b8bb61f250
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 383eafdda02f402d1c398183bfedac6dde85d9ce
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="fulltextcatalogproperty-transact-sql"></a>FULLTEXTCATALOGPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のフルテキスト カタログ プロパティについての情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FULLTEXTCATALOGPROPERTY ('catalog_name' ,'property')  
```  
  
## <a name="arguments"></a>引数  
  
> [!NOTE]  
>  将来のリリースでは、次のプロパティを削除予定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **LogSize**と**PopulateStatus**です。 新しい開発作業では、これらのプロパティの使用は避け、現在これらのプロパティのいずれかを使用しているアプリケーションは修正するようにしてください。  
  
 *catalog_name*  
 フルテキスト カタログの名前を含む式を指定します。  
  
 *プロパティ*  
 フルテキスト カタログのプロパティ名を含む式を指定します。 次の表は、プロパティと、返される情報についての説明の一覧です。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|**AccentSensitivity**|アクセントの区別の設定。<br /><br /> 0 = アクセントを区別しない<br /><br /> 1 = アクセントを区別する|  
|**IndexSize**|フルテキスト カタログの論理サイズ (MB 単位)。 セマンティック キー フレーズとドキュメントの類似性のインデックスのサイズが含まれています。<br /><br /> 詳細については、後の「解説」を参照してください。|  
|**ItemCount**|カタログのすべてのフルテキスト、キーフレーズ、ドキュメント類似性インデックスなどのインデックス項目の数。|  
|**LogSize**|旧バージョンとの互換性のためにのみサポートされています。 常に 0 を返します。<br /><br /> 関連付けられているエラー ログの一連のバイト単位のサイズ、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search サービス、フルテキスト カタログです。|  
|**MergeStatus**|マスター マージの実行状況を示します。<br /><br /> 0 = マスター マージが実行されていない<br /><br /> 1 = マスター マージが実行中|  
|**PopulateCompletionAge**|01/01/1990 00:00:00 から、最後のフルテキスト インデックス作成が完了した時刻までの時間 (秒単位)。<br /><br /> フル クロールまたは増分クロールの場合のみ更新されます。 更新するデータがなかった場合は、0 が返されます。|  
|**PopulateStatus**|0 = Idle<br /><br /> 1 = カタログ全体を作成中<br /><br /> 2 = 一時停止<br /><br /> 3 = 絞込み<br /><br /> 4 = 復旧<br /><br /> 5 = シャットダウン<br /><br /> 6 = 増分作成中<br /><br /> 7 = インデックス作成<br /><br /> 8 = ディスク容量不足、 一時停止。<br /><br /> 9 = 変更の追跡|  
|**UniqueKeyCount**|フルテキスト カタログ内にある一意のキーの数。|  
|**ImportStatus**|フルテキスト カタログがインポートされているかどうかを示します。<br /><br /> 0 = フルテキスト カタログはインポートされていません。<br /><br /> 1 = フルテキスト カタログはインポートされています。|  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="exceptions"></a>例外  
 エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ユーザーは、ユーザーが所有するまたはをユーザーが許可されているアクセス許可のセキュリティ保護可能なメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (FULLTEXTCATALOGPROPERTY など) が NULL を返す可能性があります。 詳細については、次を参照してください。 [sp_help_fulltext_catalogs & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md).  
  
## <a name="remarks"></a>解説  
 FULLTEXTCATALOGPROPERTY ('*catalog_name*'、'**IndexSize**') のように、ステータスが 4 または 6 のフラグメントのみを参照[sys.fulltext_index_fragments](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)です。 これらのフラグメントは、論理インデックスの一部です。 したがって、 **IndexSize**プロパティには、論理インデックス サイズのみが返されます。 ただし、インデックス マージ中は、実際のインデックス サイズが論理サイズの 2 倍になる場合があります。 マージ中に、フルテキスト インデックスによって使用されている実際のサイズを見つけるを使用して、 [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)システム ストアド プロシージャです。 このプロシージャは、フルテキスト インデックスに関連付けられているフラグメントをすべて調べます。 フルテキスト カタログ ファイルの拡張を制限し、マージ処理のための十分な領域を割り当てていない場合、フルテキストの作成に失敗する可能性があります。 この場合、FULLTEXTCATALOGPROPERTY ('catalog_name' ,'IndexSize') は 0 を返し、フルテキスト ログに次のエラーが書き込まれます。  
  
 `Error: 30059, Severity: 16, State: 1. A fatal error occurred during a full-text population and caused the population to be cancelled. Population type is: FULL; database name is FTS_Test (id: 13); catalog name is t1_cat (id: 5); table name t1 (id: 2105058535). Fix the errors that are logged in the full-text crawl log. Then, resume the population. The basic Transact-SQL syntax for this is: ALTER FULLTEXT INDEX ON table_name RESUME POPULATION.`  
  
 アプリケーションのチェック、ループの中で待機しないことが重要である、 **PopulateStatus**プロパティに、アイドル状態 (を示すカタログの作成が完了している) ため、これには、データベースと、フルテキストの CPU サイクル検索のプロセスとタイムアウトします。 さらに、通常は、対応を確認することをお勧め**PopulateStatus**テーブル レベルでプロパティ**TableFullTextPopulateStatus** OBJECTPROPERTYEX システム関数です。 OBJECTPROPERTYEX で、このプロパティとその他の新しいフルテキスト プロパティを使用すると、フルテキスト インデックス作成テーブルに関するより詳細な情報を取得できます。 詳細については、「[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、`Cat_Desc` という名前のフルテキスト カタログにあるフルテキスト インデックス項目の個数を返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT fulltextcatalogproperty('Cat_Desc', 'ItemCount');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [FULLTEXTSERVICEPROPERTY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_help_fulltext_catalogs および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)  
  
  

