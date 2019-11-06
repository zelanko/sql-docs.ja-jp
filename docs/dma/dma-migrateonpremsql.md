---
title: アップグレード オンプレミス SQL Server または SQL Server Data Migration Assistant を使用して Azure Vm 上に SQL Server |Microsoft Docs
description: Data Migration Assistant を使用して、以降のバージョンの SQL Server または Azure Vm 上の SQL Server には、オンプレミスの SQL Server をアップグレードする方法について説明します
ms.custom: ''
ms.date: 05/18/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: HJToland3
ms.author: jtoland
ms.openlocfilehash: 8366b04be48df3e47e9c6d531738ebebfee45da0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058825"
---
# <a name="upgrade-on-premises-sql-server-to-sql-server-or-sql-server-on-azure-vms-using-the-data-migration-assistant"></a>SQL Server または Data Migration Assistant を使用して Azure Vm 上の SQL Server にオンプレミスの SQL Server のアップグレードします。

Data Migration Assistant は、Azure Vm または Azure SQL Database で SQL Server オンプレミスと以降のバージョンの SQL Server へのアップグレードまたは SQL Server への移行のシームレスな評価を提供します。

この記事では、Data Migration Assistant を使用して、オンプレミス SQL Server 以降のバージョンの SQL Server または Azure Vm 上の SQL Server をアップグレードするための詳細な手順を説明します。

## <a name="create-a-new-migration-project"></a>新しい移行プロジェクトを作成します。

1. 左側のウィンドウで次のように選択します。**新規**(+) をクリックし、**移行**プロジェクトの種類。

2. ソースとターゲット サーバーの種類を設定**SQL Server**オンプレミスの SQL Server の新しいバージョンに、オンプレミスの SQL Server をアップグレードしているかどうか。

3. **[作成]** を選択します。

   ![移行プロジェクトを作成します。](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>ソースとターゲットを指定します。

1. ソースの SQL Server インスタンス名を入力します。、**サーバー名**フィールドに、**ソース サーバーの詳細**セクション。 

2. 選択、**認証の種類**ソース SQL Server のインスタンスによってサポートされています。

3. ターゲットでの SQL Server インスタンス名を入力、**サーバー名**フィールドに、**対象のサーバーの詳細**セクション。 

4. 選択、**認証の種類**ターゲット SQL Server のインスタンスによってサポートされています。

5. 選択して、接続を暗号化することをお勧め**接続を暗号化**で、**接続プロパティ**セクション。

6. **[次へ]** をクリックします。

   ![ソースとターゲットのページを指定します。](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>データベースを追加します。

1. のみの左側のウィンドウで、これらのデータベースを選択して移行する特定のデータベースの選択、**データベースを追加**ページ。

   移行のため既定では、ソース SQL Server インスタンス上のすべてのユーザー データベースの選択します。

2. ページの右側にある移行の設定を使用すると、次の手順に従って、データベースに適用されている移行オプションを設定できます。

   > [!NOTE]
   > 左側のウィンドウで、サーバーを選択して、移行するすべてのデータベースには、移行の設定を適用できます。 左側のウィンドウで、データベースを選択して、個々 のデータベース固有の設定で構成することもできます。

    a. 指定、**ソースとターゲットの SQL サーバーのバックアップ操作でアクセスできる場所を共有**します。 サービス アカウントが実行されているソース SQL Server のインスタンスが書き込み共有の場所での特権と、ターゲット サービス アカウントに読み取り、共有の場所での特権があることを確認してください。

    b. データと対象サーバー上のトランザクションのログ ファイルを復元する場所を指定します。

    ![[データベース] ページを追加します。](../dma/media/AddDatabases.png)

3. ソースとターゲットの SQL Server インスタンスがあるへのアクセス、共有の場所を入力、**共有場所のオプション**ボックス。

4. 選択へのアクセスをそのソースとターゲットの両方の SQL サーバーがある共有の場所を提供できない場合**ターゲット サーバーが読み取りし、からの復元を別の場所にデータベースのバックアップをコピー**します。 値を入力し、**復元オプションのバックアップの場所**ボックス。 

   Data Migration Assistant を実行しているユーザー アカウントに読み取り、バックアップの場所に特権があるかどうかを確認し、ターゲット サーバーの復元元の場所に特権を記述します。

   ![データベースのバックアップを別の場所にコピーするオプション](../dma/media/CopyDatabaseDifferentLocation.png)

5. **[次へ]** を選択します。

Data Migration Assistant は、バックアップ フォルダー、データ、およびログ ファイルの場所での検証を実行します。 いずれかの検証に失敗した場合、オプションを修正し、**次**します。

## <a name="select-logins"></a>ログインを選択します。

1. 特定のログインの移行を選択します。

   > [!IMPORTANT]
   > 移行用に選択されたデータベース内の 1 つまたは複数のユーザーにマップされるログインを選択してください。   

   既定では、移行の移行の対象にするすべての SQL Server と Windows のログインが選択されます。

2. 選択**移行を開始**します。

   ![ログインを選択して、移行を開始](../dma/media/SelectLogins.png)

## <a name="view-results"></a>結果を表示します。

移行の進行状況を監視することができます、**結果を表示**ページ。

![ビューの結果 ページ](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>移行の結果をエクスポートします。

1. クリックして**レポートをエクスポート**の下部にある、**結果を表示**移行結果を CSV ファイルに保存するページ。

2. 詳細については、ログインの移行では、保存したファイルを確認し、変更を確認します。

## <a name="see-also"></a>関連項目

- [Data Migration Assistant (DMA)](../dma/dma-overview.md)
- [Data Migration Assistant:構成設定](../dma/dma-configurationsettings.md)
- [Data Migration Assistant:ベスト プラクティス](../dma/dma-bestpractices.md)
