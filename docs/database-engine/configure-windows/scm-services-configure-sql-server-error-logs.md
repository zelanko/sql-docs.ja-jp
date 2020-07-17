---
title: SQL Server エラー ログの構成 | Microsoft Docs
description: エラー ログの再利用について説明します。 ログ ファイル サイズの最大値を設定する方法と、SQL Server がバックアップしてアーカイブする以前のログ ファイルの数を設定する方法について説明します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 060b3828c772a030ab095ae1bea857dc8eaa3b5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85651382"
---
# <a name="scm-services---configure-sql-server-error-logs"></a>SCM サービス - SQL Server エラー ログを構成する

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを再利用する方法を表示したり、変更したりする方法について説明します。  

## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>[SQL Server エラー ログの構成] ダイアログ ボックスを開くには  

1. オブジェクト エクスプローラーで、使用している SQL Server のインスタンスを展開し、 **[管理]** を展開します。次に、 **[SQL Server ログ]** を右クリックし、 **[構成]** をクリックします。

2. **[SQL Server エラー ログの構成]** ダイアログ ボックスで、次のオプションから選択します。

    a. ログ ファイルの数

      **[再利用する前に、エラー ログ ファイルの数を制限する]**

      再利用されるまでに作成されるエラー ログの数を制限する場合にオンにします。 新しいエラー ログは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを起動するたびに作成されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このチェック ボックスをオンにし、エラー ログ ファイルの最大数に別の数を指定しない限り、6 つ前までのログのバックアップが保持されます。  
  
      **[エラー ログ ファイルの最大数]**

      再利用されるまでに作成されるアーカイブ済みエラー ログ ファイルの最大数を指定します。 既定値は 6 です。現在のファイルは含まれません。 この値により、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再利用するまで保有している以前のバックアップ ログの数が決定されます。

    b. ログ ファイルのサイズ

      **エラー ログ ファイルの最大サイズ (KB 単位)**

      各ファイルのサイズは KB 単位で設定できます。 0 のままにしておくと、ログのサイズは無制限になります。
