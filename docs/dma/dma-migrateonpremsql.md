---
title: Data Migration Assistant で、オンプレミスの SQL Server の移行 |Microsoft Docs
description: Data Migration Assistant を使用して、別の SQL Server または Azure SQL Database には、オンプレミスの SQL Server を移行する方法について説明します
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 8133b4176fc8f8197cab646d51f4ece68b6250bc
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37784813"
---
# <a name="migrate-an-on-premises-sql-server-with-data-migration-assistant"></a>Data Migration Assistant で、オンプレミスの SQL Server を移行します。

この記事では、Data Migration Assistant を使用して SQL Server を移行するための手順を提供します。 Data Migration Assistant シームレスな評価と最新オンプレミス SQL Server と SQL Azure VM のデータ プラットフォームへと Azure SQL Database への移行を提供します。  

移行を実行するには、次のタスクを実行します。

- [新しい移行プロジェクトを作成します。](#create-a-new-migration-project)
- [ソースとターゲットを指定します。](#specify-source-and-target)
- [データベースを追加します。](#add-databases)
- [ログインを選択します。](#select-logins)

## <a name="create-a-new-migration-project"></a>新しい移行プロジェクトを作成します。

1. クリックして**新規**(+) クリックし、左側のウィンドウで、**移行**プロジェクトの種類。

1. ソースとターゲット サーバーの種類を設定**SQL Server**オンプレミスの SQL Server をアップグレードする場合、最新のオンプレミス SQL サーバー。

1. **[作成]** をクリックします。

   ![移行プロジェクトを作成します。](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>ソースとターゲットを指定します。

1. ソースの SQL Server インスタンス名を入力します。、**サーバー名**フィールドに、**ソース サーバーの詳細**セクション。 

1. 選択、**認証の種類**ソース SQL Server のインスタンスによってサポートされています。

1. ターゲットでの SQL Server インスタンス名を入力、**サーバー名**フィールドに、**対象のサーバーの詳細**セクション。 

1. 選択、**認証の種類**ターゲット SQL Server のインスタンスによってサポートされています。

1. 選択して、接続を暗号化することをお勧め**接続を暗号化**で、**接続プロパティ**セクション。

1. **[次へ]** をクリックします。

   ![ソースとターゲットのページを指定します。](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>データベースを追加します。

1. のみの左側のウィンドウで、これらのデータベースを選択して移行する特定のデータベースの選択、**データベースを追加**ページ。

   移行のため既定では、ソース SQL Server インスタンス上のすべてのユーザー データベースの選択します。

1. ページの右側にある移行の設定を使用すると、次の手順に従って、データベースに適用されている移行オプションを設定できます。

   > [!NOTE]
   > 左側のウィンドウで、サーバーを選択して、移行するすべてのデータベースには、移行の設定を適用できます。 左側のウィンドウで、データベースを選択して、個々 のデータベース固有の設定で構成することもできます。

 1. 指定、**ソースとターゲットの SQL サーバーのバックアップ操作でアクセスできる場所を共有**します。 サービス アカウントが実行されているソース SQL Server のインスタンスが書き込み共有の場所での特権と、ターゲット サービス アカウントに読み取り、共有の場所での特権があることを確認してください。

 1. データと対象サーバー上のトランザクションのログ ファイルを復元する場所を指定します。

    ![[データベース] ページを追加します。](../dma/media/AddDatabases.png)

1. ソースとターゲットの SQL Server インスタンスがあるへのアクセス、共有の場所を入力、**共有場所のオプション**ボックス。

1. 選択へのアクセスをそのソースとターゲットの両方の SQL サーバーがある共有の場所を提供できない場合**ターゲット サーバーが読み取りし、からの復元を別の場所にデータベースのバックアップをコピー**します。 値を入力し、**復元オプションのバックアップの場所**ボックス。 

   Data Migration Assistant を実行しているユーザー アカウントに読み取り、バックアップの場所に特権があるかどうかを確認し、ターゲット サーバーの復元元の場所に特権を記述します。

   ![データベースのバックアップを別の場所にコピーするオプション](../dma/media/CopyDatabaseDifferentLocation.png)

1. **[次へ]** をクリックします。

Data Migration Assistant の検証を行います、バックアップ フォルダーのデータとログ ファイルの場所。 オプションとをクリックして修正してください、検証が失敗した場合、**次**します。

## <a name="select-logins"></a>ログインを選択します。

1. 特定のログインの移行を選択します。

   > [!IMPORTANT]
   > 移行用に選択されたデータベース内の 1 つまたは複数のユーザーにマップされるログインを選択してください。   

   既定では、移行の移行の対象にするすべての SQL Server と Windows のログインが選択されます。

1. クリックして**移行を開始**します。

   ![ログインを選択して、移行を開始](../dma/media/SelectLogins.png)

## <a name="view-results"></a>結果を表示します。

移行の進行状況を監視することができます、**結果を表示**ページ。

![ビューの結果 ページ](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>移行の結果をエクスポートします。

1. クリックして**レポートをエクスポート**の下部にある、**結果を表示**移行結果を CSV ファイルに保存するページ。

1. 詳細については、ログインの移行では、保存したファイルを確認し、変更を確認します。

## <a name="see-also"></a>参照

[Data Migration Assistant (DMA)](../dma/dma-overview.md)

[Data Migration Assistant: 構成の設定](../dma/dma-configurationsettings.md)

[Data Migration Assistant: ベスト プラクティス](../dma/dma-bestpractices.md)
