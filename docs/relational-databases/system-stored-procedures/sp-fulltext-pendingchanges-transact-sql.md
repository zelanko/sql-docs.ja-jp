---
title: sp_fulltext_pendingchanges (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_pendingchanges_TSQL
- sp_fulltext_pendingchanges
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_pendingchanges
ms.assetid: fee042fe-4781-4a33-a01b-d98fb5629f1b
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 5519ade9d6ea17377304034e076d96e20af57409
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39558102"
---
# <a name="spfulltextpendingchanges-transact-sql"></a>sp_fulltext_pendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  変更の追跡を使用している指定のテーブルについて、保留中の挿入、更新、削除など、未処理となっている変更に関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_fulltext_pendingchanges table_id  
```  
  
## <a name="arguments"></a>引数  
 *table_id*  
 テーブルの ID を指定します。 テーブルにフルテキスト インデックスが作成されていない場合、またはテーブルで変更の追跡が有効になっていない場合は、エラーが返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**[キー]**|*|指定したテーブルからのフルテキスト キー値。|  
|**DocId**|**bigint**|キー値に対応する内部ドキュメント識別子 (DocId) 列。|  
|**ステータス**|**int**|0 = 行はフルテキスト インデックスから削除されます。<br /><br /> 1 = 行にはフルテキスト インデックスが作成されます。<br /><br /> 2 = 行は最新です。<br /><br /> -1 = 行は遷移 (一括処理されたがコミットされていない) 状態またはエラー状態にあります。|  
|**DocState**|**tinyint**|内部ドキュメント識別子 (Docld) のマップ ステータス列の行ダンプ。|  
  
 <sup>* キーのデータ型は、ベース テーブルのフルテキスト キー列のデータ型と同じです。</sup>  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="remarks"></a>コメント  
 未処理の変更がない場合、空の行セットが返されます。  
  
 フルテキスト検索のクエリを持つ行が返されない、**状態**0 の値。 この場合、行はベース テーブルから削除されており、フルテキスト インデックスからの削除を待機しています。  
  
 いくつの変更が保留中を検索する特定のテーブルを使用して、 **TableFullTextPendingChanges** OBJECTPROPERTYEX 関数のプロパティ。  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索およびセマンティック検索ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)  
  
  
