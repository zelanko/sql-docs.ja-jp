---
title: sys.syscacheobjects (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscacheobjects_TSQL
- sys.syscacheobjects
- syscacheobjects
- syscacheobjects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscacheobjects system table
- sys.syscacheobjects compatibility view
ms.assetid: 9b14f37c-b7f5-4f71-b070-cce89a83f69e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ba5cd0f3ec426e52da602098be0968569bf7c31a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831540"
---
# <a name="syssyscacheobjects-transact-sql"></a>sys.syscacheobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キャッシュの使用法に関する情報を示します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**bucketid**|**int**|バケット ID です。 値は 0 ～ディレクトリ サイズ -1 の範囲を示します。 ディレクトリ サイズは、ハッシュ テーブルのサイズです。|  
|**cacheobjtype**|**nvarchar(17)**|キャッシュ内のオブジェクトの種類です。<br /><br /> コンパイル済みプラン<br /><br /> 実行プラン<br /><br /> 解析ツリー<br /><br /> カーソル<br /><br /> 拡張ストアド プロシージャ|  
|**objtype**|**nvarchar(8)**|オブジェクトの種類です。<br /><br /> ストアド プロシージャ<br /><br /> 準備済みステートメント<br /><br /> アドホック クエリ ([!INCLUDE[tsql](../../includes/tsql-md.md)]から言語イベントとして送信された、 **sqlcmd**または**osql**ユーティリティは、リモート プロシージャ呼び出しではなく)<br /><br /> ReplProc (レプリケーション プロシージャ)<br /><br /> トリガー<br /><br /> 表示<br /><br /> 既定<br /><br /> ユーザー テーブル<br /><br /> システム テーブル<br /><br /> [確認]<br /><br /> Rule|  
|**objid**|**int**|キャッシュ内のオブジェクトを検索するために使用される主キーの 1 つです。 これは、オブジェクトに格納されている ID **sysobjects**のデータベース オブジェクト (プロシージャ、ビュー、トリガー、およびなど)。 アドホックまたは準備された SQL などのキャッシュ オブジェクトの**objid**は内部的に生成された値です。|  
|**dbid**|**smallint**|キャッシュ オブジェクトがコンパイルされたデータベース ID です。|  
|**dbidexec**|**smallint**|クエリ実行元となるデータベース ID です。<br /><br /> ほとんどのオブジェクトに対して**dbidexec**と同じ値を持つ**dbid**します。<br /><br /> システム ビュー、 **dbidexec**は、クエリを実行するためのデータベースの ID です。<br /><br /> アドホック クエリでは、 **dbidexec**は 0 です。 つまり、 **dbidexec**と同じ値を持つ**dbid**します。|  
|**uid**|**smallint**|アドホックなクエリ プランおよび使用可能になったプランのプラン作成者です。<br /><br /> -2 は、送られたバッチが暗黙的な名前解決に依存せず、複数ユーザー間での共有が可能なことを示します。 これは推奨される方法です。 他の値は、データベースのクエリを送っているユーザーのユーザー ID を示します。<br /><br /> ユーザーとロールの数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**refcounts**|**int**|このキャッシュ オブジェクトを参照している他のキャッシュ オブジェクトの数です。 1 は基になるオブジェクトであることを示します。|  
|**usecounts**|**int**|このキャッシュ オブジェクトが最初の時点から使用された回数です。|  
|**pagesused**|**int**|キャッシュ オブジェクトによって使用されたページ数です。|  
|**setopts**|**int**|コンパイル済みプランに影響する SET オプションの設定です。 この設定は、キャッシュ キーの一部です。 この列の値が変更されている場合、ユーザーが SET オプションを変更したことを示します。 これには、次の作業が含まれます。<br /><br /> **ANSI_PADDING**<br /><br /> **FORCEPLAN**<br /><br /> **CONCAT_NULL_YIELDS_NULL**<br /><br /> **ANSI_WARNINGS**<br /><br /> **ANSI_NULLS**<br /><br /> **QUOTED_IDENTIFIER**<br /><br /> **ANSI_NULL_DFLT_ON**<br /><br /> **ANSI_NULL_DFLT_OFF**|  
|**langid**|**smallint**|言語 ID です。 キャッシュ オブジェクトを作成した接続の言語の ID です。|  
|**dateformat**|**smallint**|キャッシュ オブジェクトを作成した接続の日付形式です。|  
|**status**|**int**|キャッシュ オブジェクトがカーソル プランであるかどうかを示します。 現時点では、最下位ビットのみが使用されます。|  
|**lasttime**|**bigint**|これは旧バージョンとの互換性のためにだけ用意されています。 常に 0 を返します。|  
|**maxexectime**|**bigint**|これは旧バージョンとの互換性のためにだけ用意されています。 常に 0 を返します。|  
|**avgexectime**|**bigint**|これは旧バージョンとの互換性のためにだけ用意されています。 常に 0 を返します。|  
|**lastreads**|**bigint**|これは旧バージョンとの互換性のためにだけ用意されています。 常に 0 を返します。|  
|**lastwrites**|**bigint**|これは旧バージョンとの互換性のためにだけ用意されています。 常に 0 を返します。|  
|**sqlbytes**|**int**|プロシージャの定義または送信済みバッチのバイト長です。|  
|**sql**|**nvarchar(3900)**|モジュール定義または送信済みバッチの最初の 3,900 文字です。|  
  
## <a name="see-also"></a>参照  
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  

