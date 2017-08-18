---
title: "external scripts enabled サーバー構成オプション | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords:
- external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ead16dff7247d19161395237fc135472a61740c0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="external-scripts-enabled-server-configuration-option"></a>external scripts enabled サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  **external scripts enabled** オプションを使用して、特定のリモート言語拡張機能を使用したスクリプトの実行を有効します。 このプロパティは既定でオフになっています。 セットアップでは、 **Advanced Analytics Services** がインストールされている場合にのみ、セットアップでこのプロパティをオプションで true に設定できます。  
  

 **sp_execute_external_script** プロシージャを使用して外部スクリプトを実行する前に、external script enabled オプションを有効にする必要があります。 **sp_execute_external_script** を使用して、R. などのサポートされている言語で記述されたスクリプトを実行します。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]では、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] と共にインストールされるサーバーのコンポーネントと、ワークステーションのツールと [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]の高パフォーマンスの環境にデータ サイエンティストを接続する接続ライブラリのセットから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は構成されます。  インストール、 **分析の拡張機能の高度な** 機能の中に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] R スクリプトの実行を有効に設定します。 詳細については、「 [Installing Previous Versions of SQL Server R Services](http://msdn.microsoft.com/library/48380645-9e72-4744-bebb-1c1fd8a18c43)」を参照してください。  
  
 外部スクリプトを有効にするには、次のスクリプトを実行します。  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE;  
```  
  
 この変更を有効にするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があります。  
  
## <a name="see-also"></a>参照  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  

