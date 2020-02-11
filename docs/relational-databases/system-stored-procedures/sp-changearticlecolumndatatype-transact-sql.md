---
title: sp_changearticlecolumndatatype (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: f101d9081c7eb898d43c461a3bd64eca0c043b64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67995516"
---
# <a name="sp_changearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Oracle パブリケーションのアーティクル列データ型マッピングを変更します。 このストアドプロシージャは、ディストリビューター側で任意のデータベースに対して実行されます。  
  
> [!NOTE]  
>  サポートされているパブリッシャーの種類間のデータ型マッピングは、既定で提供されています。 これらの既定の設定をオーバーライドする場合にのみ**sp_changearticlecolumndatatype**を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`Oracle パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @article = ] 'article'`アーティクルの名前を指定します。 *アーティクル*は**sysname**で、既定値はありません。  
  
`[ @column = ] 'column'`データ型マッピングを変更する列の名前を指定します。 *列*は**sysname**,、既定値はありません。  
  
`[ @type = ] 'type'`変換先列の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型の名前を指定します。 *種類*は**sysname**,、既定値は NULL です。  
  
`[ @length = ] length`変換先列の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型の長さを指定します。 *長さ*は**bigint**,、既定値は NULL です。  
  
`[ @precision = ] precision`変換先列の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型の有効桁数を指定します。 *有効桁数*は**bigint**,、既定値は NULL です。  
  
`[ @publisher = ] 'publisher'`以外の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーを指定します。 *publisher*は**sysname**で、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **** サポートされているパブリッシャーの種類 (Oracle および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 間の既定のデータ型マッピングをオーバーライドするには、Sp_changearticlecolumndatatype を使用します。 これらの既定のデータ型マッピングを表示するには、 [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)を実行します。  
  
 **sp_changearticlecolumndatatype**は、Oracle パブリッシャーに対してのみサポートされています。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリケーションに対してこのストアド プロシージャを実行すると、エラーが発生します。  
  
 変更する必要があるアーティクル列マッピングごとに**sp_changearticlecolumndatatype**を実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_changearticlecolumndatatype**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Oracle パブリッシャーのデータ型マッピング](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [レプリケーションストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
