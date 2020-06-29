---
title: パッケージのバックアップと復元 (SSIS サービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4cd6f3856b69485c01e4b38d89e2f7e2ec56f74
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424039"
---
# <a name="package-backup-and-restore-ssis-service"></a>パッケージのバックアップと復元 (SSIS サービス)
    
> [!IMPORTANT]  
>  このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]パッケージは、ファイルシステムまたは msdb (システムデータベース) に保存でき [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。 msdb に保存されたパッケージは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップおよび復元機能を使用してバックアップおよび復元できます。  
  
 msdb データベースのバックアップおよび復元の詳細については、次のトピックのいずれかを参照してください。  
  
-   [SQL Server データベースのバックアップと復元](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [システム データベースのバックアップと復元 &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、パッケージの管理に使用する **dtutil** コマンド プロンプト ユーティリティ (dtutil.exec) が付属しています。 詳細については、「 [dtutil ユーティリティ](dtutil-utility.md)」を参照してください。  
  
## <a name="configuration-files"></a>構成ファイル  
 パッケージに含まれるすべての構成ファイルはファイル システムに格納されています。 msdb データベースをバックアップするとき、これらのファイルはバックアップされません。したがって、msdb に保存されたパッケージの安全を確保するための計画の一部として、構成ファイルを定期的にバックアップする必要があります。 msdb データベースのバックアップに構成を含めるには、ファイル ベースの構成の代わりに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の構成の種類の使用を検討してください。  
  
## <a name="packages-stored-in-the-file-system"></a>ファイル システムに保存されたパッケージ  
 サーバーのファイル システムのバックアップ計画には、ファイル システムに保存されるパッケージのバックアップも含める必要があります。 既定で MsDtsSrvr.ini.xml という名前を持つ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービス構成ファイルには、このサービスで監視されるサーバー上のフォルダーが定義されています。 これらのフォルダーを必ずバックアップしてください。 さらに、パッケージをサーバー上の他のフォルダーに格納している場合は、これらのフォルダーもバックアップに含める必要があります。  
  
  
