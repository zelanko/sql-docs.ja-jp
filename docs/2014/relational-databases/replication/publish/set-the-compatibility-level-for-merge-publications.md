---
title: マージ パブリケーションの互換性レベルの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], replication
- backward compatibility [SQL Server], replication
- publications [SQL Server replication], backward compatibility
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7aecff691139b1041a928c42c3df2987c992cd91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68199317"
---
# <a name="set-the-compatibility-level-for-merge-publications"></a>マージ パブリケーションの互換性レベルの設定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ パブリケーションの互換性レベルを設定する方法について説明します。 マージ レプリケーションでは、パブリケーションの互換性レベルを使用して、指定されたデータベースのパブリケーションで使用できる機能を決定します。  
  
 **このトピックの内容**  
  
-   **マージパブリケーションの互換性レベルを設定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードの **[サブスクライバーの種類]** ページで互換性レベルを設定します。 このウィザードへのアクセスの詳細については、「 [Create a Publication](create-a-publication.md)を使用して、マージ パブリケーションの互換性レベルを設定する方法について説明します。 パブリケーション スナップショットの作成後、互換性レベルを上げることはできますが、下げることはできません。 
  **[パブリケーションのプロパティ - **Publication>]** ダイアログ ボックスの \<[全般]** ページで互換性レベルを上げます。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。 パブリケーションの互換性レベルを上げた場合、設定した互換性レベルよりも前のバージョンを実行しているサーバーでは、既存のサブスクリプションを同期できなくなります。  
  
> [!NOTE]  
>  互換性レベルはパブリケーションの他のプロパティ、および有効になるアーティクルのプロパティと密接に関連しているため、互換性レベルとその他のプロパティをこのダイアログ ボックスで同時に変更しないでください。 プロパティの変更後、パブリケーションのスナップショットを再生成する必要があります。  
  
#### <a name="to-set-the-publication-compatibility-level"></a>パブリケーションの互換性レベルを設定するには  
  
-   パブリケーションの新規作成ウィザードの **[サブスクライバーの種類]** ページで、パブリケーションがサポートするサブスクライバーの種類を選択します。  
  
#### <a name="to-increase-the-publication-compatibility-level"></a>パブリケーションの互換性レベルを上げるには  
  
-   
  **[パブリケーションのプロパティ - **Publication>]** ダイアログ ボックスの \<[全般]** ページで、**[互換性レベル]** を選択します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 マージ パブリケーションの互換性レベルは、パブリケーションを作成したときにプログラムで設定するか、または後でプログラムから変更できます。 レプリケーション ストアド プロシージャを使用して、このパブリケーション プロパティを設定または変更できます。  
  
#### <a name="to-set-the-publication-compatibility-level-for-a-merge-publication"></a>マージ パブリケーションのパブリケーション互換性レベルを設定するには  
  
1.  パブリッシャーで[sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。このとき、の値**@publication_compatibility_level**を指定して、パブリケーションを以前の[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]バージョンのと互換性があるようにします。 詳しくは、「 [Create a Publication](create-a-publication.md)」をご覧ください。  
  
#### <a name="to-change-the-publication-compatibility-level-of-a-merge-publication"></a>マージ パブリケーションのパブリケーション互換性レベルを変更するには  
  
1.  [&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行 sp_changemergepublication、に**@property** **publication_compatibility_level**を、に**@value**適切なパブリケーション互換性レベルを指定します。  
  
#### <a name="to-determine-the-publication-compatibility-level-of-a-merge-publication"></a>マージ パブリケーションのパブリケーション互換性レベルを確認するには  
  
1.  目的のパブリケーションを指定して、[sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql) を実行します。  
  
2.  結果セットの **backward_comp_level** 列で、パブリケーションの互換性レベルを調べます。  
  
###  <a name="TsqlExample"></a>例 (Transact-sql)  
 次の例では、マージ パブリケーションを作成して、パブリケーションの互換性レベルを設定します。  
  
```  
-- To avoid storing the login and password in the script file, the values   
-- are passed into SQLCMD as scripting variables. For information about   
-- how to use scripting variables on the command line and in SQL Server  
-- Management Studio, see the "Executing Replication Scripts" section in  
-- the topic "Programming Replication Using System Stored Procedures".  
  
--Add a new merge publication.  
DECLARE @publicationDB AS sysname;  
DECLARE @publication AS sysname;  
DECLARE @login AS sysname;  
DECLARE @password AS sysname;  
SET @publicationDB = N'AdventureWorks2012';   
SET @publication = N'AdvWorksSalesOrdersMerge'   
SET @login = $(Login);  
SET @password = $(Password);  
  
-- Create a new merge publication.   
USE [AdventureWorks2012]  
EXEC sp_addmergepublication   
@publication = @publication,   
-- Set the compatibility level to SQL Server 2014.  
@publication_compatibility_level = '120RTM';   
  
-- Create the snapshot job for the publication.  
EXEC sp_addpublication_snapshot   
@publication = @publication,  
@job_login = @login,  
@job_password = @password;  
GO  
```  
  
 次の例では、マージ パブリケーションのパブリケーション互換性レベルを変更します。  
  
> [!NOTE]  
>  パブリケーションで特定の互換性レベルを必要とする機能を使用していると、パブリケーションの互換性レベルの変更が許可されない場合があります。 詳しくは、「[レプリケーションの旧バージョンとの互換性](../replication-backward-compatibility.md)」をご覧ください。  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
  
-- Change the publication compatibility level to   
-- SQL Server 2012.  
EXEC sp_changemergepublication   
@publication = @publication,   
@property = N'publication_compatibility_level',   
@value = N'110RTM';  
GO  
  
```  
  
 次の例では、マージ パブリケーションの現在のパブリケーション互換性レベルが返されます。  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
EXEC sp_helpmergepublication   
@publication = @publication;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [パブリケーションを作成する](create-a-publication.md)  
  
  
