---
title: default full-text language サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- default full-text language option
ms.assetid: 0fa8785b-0830-4a52-aff5-fcf8268b72fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec0736326a4da0708d125bfc480996d54bb86c8a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935733"
---
# <a name="configure-the-default-full-text-language-server-configuration-option"></a>default full-text language サーバー構成オプションの構成
  このトピック `default full-text language` で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、のサーバー構成オプションを構成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。 オプションでは、 `default full-text language` フルテキストインデックスの既定の言語値を指定します。 言語分析は、フルテキスト インデックスが作成されるすべてのデータに対して実行され、データの言語に依存します。 このオプションの既定値は、サーバーの言語です。 のローカライズ版では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 適切な一致が存在する場合、セットアップによって `default full-text language` オプションがサーバーの言語に設定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズされていないバージョンでは、`default full-text language` オプションは英語になります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Recommendations (推奨事項)](#Recommendations)  
  
     [Security](#Security)  
  
-   **以下を使用して default full-text language オプションを構成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報:** [default full-text language オプションを構成した後](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   フルテキストインデックスでは、オプションの値が使用されています。このオプションを使用し `default full-text language` て、列に言語が指定されていない場合、CREATE フルテキストインデックスまたは ALTER フルテキストインデックスステートメントの言語**language_term**オプションです。 既定のフルテキスト言語がサポートされていない場合や、言語分析パッケージがない場合は、CREATE または ALTER 操作に失敗し、指定した言語が有効でないというエラー メッセージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって表示されます。  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> 推奨事項  
  
-   このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。  
  
-   オプションには `default full-text language` LCID 値が必要です。 サポートされている LCID とその関連言語の一覧については、「 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)サーバー構成オプションを構成する方法について説明します。 他の言語も独立ソフトウェア ベンダーから入手可能です。 特定の言語の方言が見つからない場合は、Full-Text Engine によって自動的にプライマリ言語に切り替えられます。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-configure-the-default-full-text-language-option"></a>default full-text language オプションを構成するには  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  **[詳細設定]** ノードをクリックします。  
  
3.  [その他] の **[既定のフルテキスト言語]** を使用して、フルテキスト インデックスが作成される列の既定の言語の値を指定します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-configure-the-default-full-text-language-option"></a>default full-text language オプションを構成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `default full-text` オプションの値をオランダ語 (`1043`) に設定する方法を示します。  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'default full-text language', 1043 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。  
  
##  <a name="follow-up-after-you-configure-the-default-full-text-language-option"></a><a name="FollowUp"></a>補足情報: default full-text language オプションを構成した後  
 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## <a name="see-also"></a>参照  
 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
