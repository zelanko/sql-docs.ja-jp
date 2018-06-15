---
title: sp_syscollector_update_collector_type (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collector_type_TSQL
- sp_syscollector_update_collector_type
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 3c414dfd-d9ca-4320-81aa-949465b967bf
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9013eb0eccd260c2f90d8f2858ab9ae2871a6c6f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252314"
---
# <a name="spsyscollectorupdatecollectortype-transact-sql"></a>sp_syscollector_update_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション項目のコレクター型を更新します。 指定された名前と、コレクター型の GUID、収集とアップロード パッケージ、パラメーター スキーマ、パラメーター フォーマッタ スキーマなど、コレクター型の構成を更新します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_update_collector_type [ @collector_type_uid = ] 'collector_type_uid' OUTPUT  
          , [ @name = ] 'name'  
          , [ @parameter_schema = ] 'parameter_schema'  
          , [ @collection_package_id = ] collection_package_id  
          , [ @upload_package_id = ] upload_package_id  
```  
  
## <a name="arguments"></a>引数  
 [  **@collector_type_uid =** ] **'***collector_type_uid***'**  
 コレクター型の GUID です。 *collector_type_uid*は**uniqueidentifier**、しする場合は NULL に自動的に作成され、出力として返されます。  
  
 [ **@name =** ] **'***name***'**  
 コレクター型の名前を指定します。 *名前*は**sysname**と指定する必要があります。  
  
 [  **@parameter_schema =** ] **'***parameter_schema***'**  
 このコレクター型の XML スキーマを指定します。 *parameter_schema*は**xml**し、特定のコレクター型に必要な場合があります。 必要でない場合は、この引数を NULL にできます。  
  
 [ **@collection_package_id =** ] *collection_package_id*  
 ローカル一意識別子が指すは、[!INCLUDE[ssIS](../../includes/ssis-md.md)]コレクション パッケージのコレクション セットで使用します。 *collection_package_id*は**uniqueidentifer**が必要とします。 値を取得する*collection_package_id*、msdb データベースの dbo.syscollector_collector_types システム ビューにクエリします。  
  
 [ **@upload_package_id =** ] *upload_package_id*  
 ローカル一意識別子が指すは、[!INCLUDE[ssIS](../../includes/ssis-md.md)]コレクション セットによって使用されるパッケージをアップロードします。 *upload_package_id*は**uniqueidentifier**が必要とします。 値を取得する*upload_package_id*、msdb データベースの dbo.syscollector_collector_types システム ビューにクエリします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **dc_admin** (EXECUTE 権限) を持つ固定データベース ロール。  
  
## <a name="example"></a>例  
 次の例では、ジェネリック T-SQL Query コレクター型を更新します  (この例では、ジェネリック T-SQL Query コレクター型の既定のスキーマを使用しています)。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collector_type  
@collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
@name = 'Generic T-SQL Query Collector Type',  
@parameter_schema = '<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="DataCollectorType">  
  <xs:element name="TSQLQueryCollector">  
<xs:complexType>  
  <xs:sequence>  
<xs:element name="Query" minOccurs="1" maxOccurs="unbounded">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Value" type="xs:string" />  
  <xs:element name="OutputTable" type="xs:string" />  
</xs:sequence>  
  </xs:complexType>  
</xs:element>  
<xs:element name="Databases" minOccurs="0" maxOccurs="1">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Database" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
</xs:sequence>  
<xs:attribute name="UseSystemDatabases" type="xs:boolean" use="optional" />  
<xs:attribute name="UseUserDatabases" type="xs:boolean" use="optional" />  
  </xs:complexType>  
</xs:element>  
  </xs:sequence>  
</xs:complexType>  
  </xs:element>  
</xs:schema>',  
@collection_package_id = '292B1476-0F46-4490-A9B7-6DB724DE3C0B',  
@upload_package_id = '6EB73801-39CF-489C-B682-497350C939F0';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データ コレクション](../../relational-databases/data-collection/data-collection.md)  
  
  
