---
title: SQL Server エラー ログの構成 | Microsoft Docs
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a4da039e1fcc41570fcead275bbe4b2cb0be5797
ms.sourcegitcommit: 0d89bcaebdf87db3bd26db2ca263be9c671b0220
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2019
ms.locfileid: "68731098"
---
# <a name="scm-services---configure-sql-server-error-logs"></a>SCM サービス - SQL Server エラー ログを構成する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを再利用する方法を表示したり、変更したりする方法について説明します。  

## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>[SQL Server エラー ログの構成] ダイアログ ボックスを開くには  

1. オブジェクト エクスプローラーで、使用している SQL Server のインスタンスを展開し、 **[管理]** を展開します。次に、 **[SQL Server ログ]** を右クリックし、 **[構成]** をクリックします。

2. **[SQL Server エラー ログの構成]** ダイアログ ボックスで、次のオプションから選択します。

    A. ログ ファイルの数

      **[再利用する前に、エラー ログ ファイルの数を制限する]**

      再利用されるまでに作成されるエラー ログの数を制限する場合にオンにします。 新しいエラー ログは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを起動するたびに作成されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このチェック ボックスをオンにし、エラー ログ ファイルの最大数に別の数を指定しない限り、6 つ前までのログのバックアップが保持されます。  
  
      **[エラー ログ ファイルの最大数]**

      再利用されるまでに作成されるエラー ログ ファイルの最大数を指定します。 既定値は 6 で、これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再利用するまで保有している以前のバックアップ ログの数と同じです。

    B. ログ ファイルのサイズ

      **エラー ログ ファイルの最大サイズ (KB 単位)**

      各ファイルのサイズは KB 単位で設定できます。 0 のままにしておくと、ログのサイズは無制限になります。
