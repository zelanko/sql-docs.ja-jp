---
title: sp_changearticlecolumndatatype (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 04da16aadb8caf05ee28882c11658e81bf5bbfe7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32989647"
---
# <a name="spchangearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Oracle パブリケーションのアーティクル列データ型マッピングを変更します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
> [!NOTE]  
>  サポートされているパブリッシャーの種類の間におけるデータ型マッピングは、既定のものが用意されています。 使用して**sp_changearticlecolumndatatype**既定の設定をオーバーライドする場合にのみです。  
  
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
 [  **@publication=** ] **'***パブリケーション***'**  
 Oracle パブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article =** ] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [ **@column**=] **'***列***'**  
 データ型マッピングを変更する列の名前を指定します。 *列*は**sysname**、既定値はありません。  
  
 [ **@type** =] **'***型***'**  
 名前を指定、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先列のデータ型。 *型*は**sysname**、既定値は NULL です。  
  
 [ **@length** =]*長さ*  
 変換先列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の長さを指定します。 *長さ*は**bigint**、既定値は NULL です。  
  
 [ **@precision**=]*精度*  
 変換先列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の有効桁数を指定します。 *有効桁数*は**bigint**、既定値は NULL です。  
  
 [ **@publisher**=] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **Sp_changearticlecolumndatatype**サポートされている発行元の型の間の既定のデータ型マッピングを上書きに使用されます (Oracle と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。 この既定のデータ型マッピングを表示するには、実行[sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)です。  
  
 **sp_changearticlecolumndatatype**は Oracle パブリッシャーに対してのみサポートされます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリケーションに対してこのストアド プロシージャを実行すると、エラーが発生します。  
  
 **sp_changearticlecolumndatatype**を変更するアーティクル列マッピングごとに実行する必要があります。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changearticlecolumndatatype**です。  
  
## <a name="see-also"></a>参照  
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
