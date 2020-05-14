---
title: Microsoft Azure サブスクリプションへの接続 | Microsoft Docs
description: SQL Server のインスタンスに Azure BLOB コンテナーを登録します。これにより、Shared Access Signature、格納されたアクセス ポリシー、および SQL Server 資格情報が作成されます。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cca5a270-643f-4677-8802-98464f19f82a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 974086bc61e2f40819c77693a6033aac512893ac
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829760"
---
# <a name="connect-to-a-microsoft-azure-subscription"></a>Microsoft Azure サブスクリプションへの接続
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**Microsoft サブスクリプションへの接続** を使用して、既存の Azure BLOB コンテナーを SQL Server のインスタンスに登録します。  ダイアログ ボックスでは、Shared Access Signature と格納されたアクセス ポリシーが Azure BLOB コンテナーに作成された後に、SQL Server 資格情報が作成されます。  このダイアログ ボックスは、SQL Server Management Studio からバックアップ タスクまたは復元タスクを使用する際に表示され、その操作には URL デバイスが必要です。

## <a name="limitation"></a>制限事項
**Microsoft サブスクリプションへの接続** は、Service Management (クラシック) デプロイメント モデルを使って作成された Azure Storage アカウントでのみ機能します。  Azure デプロイメント モデルに関する詳細については、「 [Azure Resource Manager とクラシック デプロイ](https://azure.microsoft.com/documentation/articles/resource-manager-deployment-model/)」を参照してください。

## <a name="options"></a>Options
**サインイン**     
適切な Azure アカウントでサインインします。

**使用するサブスクリプションの選択**      
ドロップダウン リストから目的のサブスクリプションを選択します。

**ストレージ アカウントの選択**  
ドロップダウン リストからストレージ アカウントを選択します。

**BLOB コンテナーの選択**   
ドロップダウン リストから目的の BLOB コンテナーを選択します。

**Shared Access Policy の有効期限**   
Shared Access Policy は、指定された日付に期限が切れます。  既定の有効期限の日付は、作成日から 1 年後です。  必要に応じて変更します。

**生成された Shared Access Signature**   
生成された Shared Access Signature は、リッチ テキスト ボックスに表示されます。

**資格情報の作成**   
ボタンを使って、格納されたアクセス ポリシーおよび Shared Access Signature が生成された後に SQL Server 資格情報が作成されます。
