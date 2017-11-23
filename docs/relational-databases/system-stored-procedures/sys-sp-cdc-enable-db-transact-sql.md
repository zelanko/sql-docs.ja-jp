---
title: "sys.sp_cdc_enable_db (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cdc_enable_db_TSQL
- sp_cdc_enable_db
- sys.sp_cdc_enable_db
- sys.sp_cdc_enable_db_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sp_cdc_enable_db
- change data capture [SQL Server], enabling databases
- sp_cdc_enable_db
ms.assetid: 176d83b3-493d-43cd-800e-aa123c3bdf17
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3dc426d71707da2330197a2c5040f800efa54a21
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysspcdcenabledb-transact-sql"></a>sys.sp_cdc_enable_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに対して変更データ キャプチャを有効にします。 データベース内のテーブルの変更データ キャプチャを有効にするには、まずそのデータベースに対してこの手順を実行する必要があります。 変更データ キャプチャは、有効なテーブルに対して適用された挿入、更新、削除の各アクティビティを記録し、変更の詳細を、利用しやすいリレーショナル形式で格納します。 変更された行に対応する列情報が、その変更をターゲット環境に適用するために必要なメタデータと共にキャプチャされます。その際、追跡対象となるソース テーブルの列構造はミラー化されます。  
  
> [!IMPORTANT]  
>  変更データ キャプチャは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディッションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_enable_db  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 変更データ キャプチャを有効にすることはできません[システム データベース](../../relational-databases/databases/system-databases.md)またはディストリビューション データベースです。  
  
 sys.sp_cdc_enable_db を実行すると、メタデータ テーブルや DDL トリガーなど、データベース全体のスコープを持つ変更データ キャプチャ オブジェクトが作成されます。 また、cdc スキーマおよび cdc データベース ユーザーが作成され、データベース内のエントリの is_cdc_enabled 列を設定、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューを 1 です。  
  
## <a name="permissions"></a>Permissions  
 sysadmin 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、変更データ キャプチャを有効にします。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_enable_db;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_disable_db &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)  
  
  
