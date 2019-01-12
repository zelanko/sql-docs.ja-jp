---
title: sp_changearticlecolumndatatype (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 07213247345280e992c2fbd5552d5cdfb96747ab
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133562"
---
# <a name="spchangearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Oracle パブリケーションのアーティクル列データ型マッピングを変更します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
> [!NOTE]  
>  サポートされているパブリッシャーの種類の間におけるデータ型マッピングは、既定のものが用意されています。 使用**sp_changearticlecolumndatatype**これら既定の設定をオーバーライドする場合のみです。  
  
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
 [  **@publication=** ] **'**_パブリケーション_**'**  
 Oracle パブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article =** ] **'**_記事_**'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [ **@column**=] **'**_列_**'**  
 データ型マッピングを変更する列の名前を指定します。 *列*は**sysname**、既定値はありません。  
  
 [ **@type** =] **'**_型_**'**  
 名前を指定します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先列のデータ型。 *型*は**sysname**、既定値は NULL です。  
  
 [ **@length** =]*長さ*  
 変換先列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の長さを指定します。 *長さ*は**bigint**、既定値は NULL です。  
  
 [ **@precision**=]*有効桁数*  
 変換先列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の有効桁数を指定します。 *有効桁数*は**bigint**、既定値は NULL です。  
  
 [ **@publisher**=] **'**_パブリッシャー_**'**  
 以外を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **Sp_changearticlecolumndatatype**サポートされている発行元の型の間の既定のデータ型マッピングを上書きに使用されます (Oracle と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。 これら既定のデータ型マッピングを表示する実行[sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)します。  
  
 **sp_changearticlecolumndatatype**は Oracle パブリッシャーに対してのみサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリケーションに対してこのストアド プロシージャを実行すると、エラーが発生します。  
  
 **sp_changearticlecolumndatatype**を変更するアーティクル列マッピングごとに実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changearticlecolumndatatype**します。  
  
## <a name="see-also"></a>参照  
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
