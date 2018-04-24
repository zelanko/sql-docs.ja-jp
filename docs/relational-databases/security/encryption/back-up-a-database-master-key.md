---
title: データベース マスター キーのバックアップ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: security
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6cec5807dae39b49815e87ba1a519233868f463c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="back-up-a-database-master-key"></a>データベース マスター キーのバックアップ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用してデータベース マスター キーをバックアップする方法について説明します。 データベース マスター キーは、データベース内の他のキーや証明書を暗号化する際に使用します。 データベース マスター キーが削除されるか破損すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、暗号化されたキーの暗号化を解除できなくなる場合があります。さらに、そのキーを使用して暗号化されたデータは事実上失われます。 このため、データベース マスター キーはバックアップして、安全な別の場所に保存しておく必要があります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   [Transact-SQL を使用してデータベース マスター キーをバックアップするには](#Procedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   マスター キーは開かれている必要があります。したがって、バックアップ前に暗号化を解除する必要があります。 マスター キーがサービス マスター キーで暗号化されている場合は、明示的に開く必要はありません。 パスワードのみで暗号化されている場合は、明示的に開く必要があります。  
  
-   マスター キーは作成後すぐにバックアップし、安全な別の場所に保存することをお勧めします。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 データベースに対する CONTROL 権限が必要です。  
  
##  <a name="Procedure"></a> Transact-SQL を備えた SQL Server Management Studio の使用  
  
#### <a name="to-back-up-the-database-master-key"></a>データベース マスター キーをバックアップするには  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、バックアップするデータベース マスター キーが格納されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続します。  
  
2.  バックアップ メディアでデータベース マスター キーの暗号化に使用するパスワードを指定します。 このパスワードに対しては、複雑性がチェックされます。  
  
3.  バックアップしたキーのコピーを保存するためにリムーバブル バックアップ メディアを用意します。  
  
4.  キーのバックアップを作成する NTFS ディレクトリを指定します。 このディレクトリは、次の手順で指定するファイルの作成先となります。 このディレクトリは、制限の厳しいアクセス制御リスト (ACL) で保護する必要があります。  
  
5.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。  
  
6.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
7.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  キーのファイル パスとキーのパスワード (存在する場合) は、実際は上に示したものと異なります。 両方がサーバーとキーのセットアップで固有であることをご確認ください。  
  
8.  ファイルをバックアップ メディアにコピーして、コピーしたファイルを確認します。  
  
9. バックアップを安全な場所に保存します。  
  
 詳細については、「[OPEN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md)」と「[BACKUP MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md)」を参照してください。  
  
  
