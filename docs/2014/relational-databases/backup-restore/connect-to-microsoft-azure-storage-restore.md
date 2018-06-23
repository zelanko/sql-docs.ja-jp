---
title: Windows への接続 Azure ストレージ (復元) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 64e03f278465d79df789f5e9b79d95eb0ad4a7c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178456"
---
# <a name="connect-to-windows-azure-storage-restore"></a>Windows Azure ストレージへの接続 (復元)
  このダイアログ ボックスを使用すると、Windows Azure ストレージ アカウントのファイル ストレージを取得するために、Windows Azure ストレージ アカウント情報への接続を指定できます。 必要な情報を指定した後、 **[接続]** をクリックして Windows Azure ストレージへの接続を確立します。  
  
## <a name="windows-azure-storage-account"></a>Windows Azure ストレージ アカウント  
 **[ストレージ アカウント]**  
 使用する Windows Azure ストレージ アカウントの名前を選択、入力、または貼り付けます。 ドロップダウン リストに、以前に使用したアカウントが表示されます。  
  
 **アカウント キー**  
 Windows Azure ストレージ アカウントのアクセス キーを指定します。  
  
 **[安全なエンドポイントを使用する (HTTPS)]** チェック ボックス  
 Windows Azure ストレージへのセキュリティで保護された接続を確立するには、チェック ボックスをオンにします (推奨)。  
  
 **[アカウント キーを保存する]** チェック ボックス  
 このストレージ アカウントのアクセス キーを SQL Server に記憶させる場合は、このチェック ボックスをオンにします。  
  
### <a name="sql-credential"></a>[SQL 資格情報]  
 **[既存の資格情報の選択]**  
 ストレージ アカウントおよびアカウント キー情報と一致する既存の SQL 資格情報を選択します。  
  
 **[新しい資格情報の作成]**  
 ストレージ アカウントとアカウント キー情報を使用して新しい資格情報を作成するには、このオプションを選択します。 **[資格情報名]** フィールドに新しい資格情報の名前を指定します。  
  
  