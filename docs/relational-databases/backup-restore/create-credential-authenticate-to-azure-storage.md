---
title: "資格情報の作成- Azure ストレージに対する認証 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3df7cdfdd5ac69eeed14bb97d176ae4497f73cee
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="create-credential---authenticate-to-azure-storage"></a>資格情報の作成- Azure ストレージに対する認証
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[Backup To URL - 資格情報の作成]** ダイアログ ボックスを使用すると、新しい SQL 資格情報を作成できます。  
  
 このダイアログ ボックスを使用して資格情報を作成する場合、サブスクリプションとストレージ アカウント情報を検証するために、ローカル証明書ストアに追加した Windows Azure 管理証明書、またはコンピューターにダウンロードした公開プロファイルを指定する必要があります。  
  
 **[SQL 資格情報]**  
 作成する SQL 資格情報の名前を指定します。  
  
## <a name="windows-azure-credentials"></a>Windows Azure 資格情報  
 **[管理証明書]**  
 このオプションを使用して、Windows Azure からの管理証明書に一致するローカル証明書ストアの証明書を指定します。 Windows Azure 管理証明書の詳細については、「 [Windows Azure の管理証明書の作成とアップロード](http://go.microsoft.com/fwlink/?LinkId=320781)」を参照してください。  
  
 **サブスクリプション**  
 ローカル証明書ストアの管理証明書と一致する Windows Azure サブスクリプション ID を選択、入力、または貼り付けます。  
  
 **[公開プロファイル]**  
 コンピューターにダウンロードした公開プロファイルがある場合は、このオプションを使用します。 このオプションを使用すると、サブスクリプション ID と証明書が自動的に入力されます。  
  
> [!CAUTION]  
>  SQL Server では現在、公開プロファイルのバージョン 2.0 がサポートされています。 公開プロファイルのサポート対象バージョンをダウンロードするには、「 [公開プロファイルのバージョン 2.0 のダウンロード](http://go.microsoft.com/fwlink/?LinkId=396421)」をご覧ください。  
  
## <a name="storage-account"></a>ストレージ アカウント  
 バックアップ ファイルを格納するために使用するストレージ アカウントを選択します。  
  
  
