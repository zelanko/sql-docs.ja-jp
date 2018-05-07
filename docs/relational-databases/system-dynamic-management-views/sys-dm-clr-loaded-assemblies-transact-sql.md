---
title: sys.dm_clr_loaded_assemblies (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_clr_loaded_assemblies
- sys.dm_clr_loaded_assemblies_TSQL
- dm_clr_loaded_assemblies_TSQL
- sys.dm_clr_loaded_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_loaded_assemblies dynamic management view
ms.assetid: 8523d8db-d8a0-4b1f-ae19-6705d633e0a6
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5670bba30bc3d110d362e36c2ee27180ea18847b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmclrloadedassemblies-transact-sql"></a>sys.dm_clr_loaded_assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーのアドレス空間に読み込まれたマネージ ユーザー アセンブリごとに 1 行のデータを返します。 マネージ データベース オブジェクトで実行されているを理解し、CLR 統合のトラブルシューティングを行うには、このビューを使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 アセンブリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ データベース オブジェクトの定義や配置のために使用されるマネージ コード DLL ファイルです。 これらのマネージ データベース オブジェクトのいずれかをユーザーが実行されるたびに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、CLR がマネージ データベース オブジェクトが定義されているアセンブリ (とその参照) を読み込みます。 アセンブリは、パフォーマンス向上のために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込まれたままになるので、その後は、アセンブリを再度読み込まなくても、アセンブリに含まれているマネージ データベース オブジェクトを呼び出すことができます。 アセンブリがまでアンロードされません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリが不足します。 アセンブリと CLR 統合の詳細については、次を参照してください。 [CLR ホスト環境](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)です。 マネージ データベース オブジェクトの詳細については、次を参照してください。[共通言語ランタイムによるデータベース オブジェクトの構築&#40;CLR&#41;統合](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)です。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|読み込まれたアセンブリの ID。 **Assembly_id**でアセンブリに関する詳細情報を検索するために使用する、 [sys.assemblies &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)カタログ ビューです。 なお、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)カタログは、現在のデータベースのみでアセンブリを示しています。 **Sqs.dm_clr_loaded_assemblies**ビューは、サーバーにすべての読み込まれたアセンブリを表示します。|  
|**appdomain_address**|**int**|アプリケーション ドメインのアドレス (**AppDomain**) でアセンブリが読み込まれています。 1 人のユーザーが所有するすべてのアセンブリは、常に同じに読み込まれた**AppDomain**です。 **Appdomain_address**に関する詳細情報を参照に使用できる、 **AppDomain**で、 [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md)ビュー。|  
|**load_time**|**datetime**|アセンブリが読み込まれた時刻。 アセンブリが、まで読み込まれたままことに注意してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリが不足し、アンロード、 **AppDomain**です。 監視することができます**load_time**頻度を理解する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリが不足し、アンロード、 **AppDomain**です。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 **Dm_clr_loaded_assemblies.appdomain_address**ビューと多対一関係のある**dm_clr_appdomains.appdomain_address**です。 **Dm_clr_loaded_assemblies.assembly_id**ビューと一対多関係にある**sys.assemblies.assembly_id**です。  
  
## <a name="examples"></a>使用例  
 次の例は、現在読み込まれている現在のデータベースのすべてのアセンブリの詳細を表示する方法を示しています。  
  
```  
 SELECT a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
FROM sys.dm_clr_loaded_assemblies AS l   
INNER JOIN sys.assemblies AS a  
ON l.assembly_id = a.assembly_id;  
```  
  
 次の例の詳細を表示する方法を示しています、 **AppDomain**で、特定のアセンブリが読み込まれています。  
  
```  
SELECT appdomain_id, creation_time, db_id, user_id, state  
FROM sys.dm_clr_appdomains AS a  
WHERE appdomain_address =   
(SELECT appdomain_address   
 FROM sys.dm_clr_loaded_assemblies  
 WHERE assembly_id = 555);  
```  
  
## <a name="see-also"></a>参照  
 [共通言語ランタイム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
