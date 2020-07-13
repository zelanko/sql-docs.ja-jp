---
title: ノートブックを管理する方法
description: Azure Data Studio でノートブックを管理する方法について学習します。 これには、ノートブックを開く、ノートブックの保存、SQL 接続または Python カーネルの変更などが含まれます。
author: markingmyname
ms.author: maghan
ms.reviewer: achatter, alayu, mikeray
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: azure-data-studio
ms.technology: ''
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: 326e0b0afc4809d13cf2fdfdbd76f53dafe1cbb9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774585"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Azure Data Studio でノートブックを管理する方法

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

この記事では、Azure Data Studio でノートブック ファイルを開いて保存する方法について示します。 また、SQL Server への接続または Python カーネルを変更する方法も示します。

## <a name="open-a-notebook"></a>ノートブックを開く

**[ノートブックを開く]** ダイアログを開くには、いくつかの方法があります。 [ファイル] メニュー、ダッシュボード、コマンド パレットを使用できます。 次のセクションでは、各メソッドについて説明します。

### <a name="file-menu"></a>[ファイル] メニュー

[ファイル] メニューで **[ファイルを開く]** を選択します (Windows の場合は Ctrl + O キー、Mac の場合は Cmd + O キー)。

![[ファイルを開く] を選択して [ファイルを開く] ダイアログを開く](./media/notebooks-manage-sql-server/open-file-1.png)

### <a name="dashboard"></a>ダッシュボード

ダッシュボードで **[ノートブックを開く]** をクリックして、[ファイルを開く] ダイアログを開きます。

![ダッシュボードで [ノートブックを開く] を選択して [ファイルを開く] ダイアログを開く](./media/notebooks-manage-sql-server/open-file-2.png) 

### <a name="command-palette"></a>コマンド パレット

コマンド パレットから「**File: Open**」コマンドを使用します (Windows の場合は Ctrl + Shift + P キー、Mac の場合は Cmd + Shift + P キーと入力)。

![コマンド パレットに「File: Open」と入力し、[ファイルを開く] ダイアログを開く](./media/notebooks-manage-sql-server/open-file-3.png)

## <a name="save-a-notebook"></a>ノートブックを保存する

現在、ノートブックを保存する方法は 1 つあります。 ノートブックのツール バーから **[保存]** を選択します。

![ノートブックのツール バーの [保存] を選択してファイルを保存する](./media/notebooks-manage-sql-server/save-file-1.png)

> [!NOTE]
> 現在、次のメソッドではノートブックへの変更は保存されません。
>
> - [ファイル] メニューの **[ファイルの保存]** 、 **[名前を付けて保存]** 、 **[すべてのファイルを保存]** コマンド。
> - コマンド パレットに入力した「**File: Save**」コマンド。

## <a name="change-the-sql-connection"></a>SQL 接続を変更する

ノートブックの SQL 接続を変更するには、次のようにします。

1. ノートブック ツール バーから **[アタッチ先]** メニューを選択し、 **[接続の変更]** を選択します。

   ![ノートブックのツール バーから [アタッチ先] メニューをクリックする](./media/notebooks-manage-sql-server/select-attach-to-1.png)

2. これで最近使用した接続サーバーを選択するか、新しい接続の詳細を入力して接続できます。

   ![[アタッチ先] メニューからサーバーを選択する](./media/notebooks-manage-sql-server/select-attach-to-2.png)

## <a name="change-the-python-kernel"></a>Python カーネルを変更する

Azure Data Studio を初めて開いたとき、 **[ノートブック用 Python の構成]** ページが表示されます。 次のいずれかを選択できます。

- **[新しい Python インストール]** を選択して、Azure Data Studio 用の Python の新しいコピーをインストールする
- **[既存の Python インストールを使用する]** を選択して、Azure Data Studio で使用する既存の Python インストールのパスを指定する

アクティブな Python カーネルの場所とバージョンを表示するには、コード セルを作成し、次の Python コマンドを実行します。

```python
import os
import sys
print(sys.version_info)
print(os.path.dirname(sys.executable))
```

別の Python インストールに変更するには、次のようにします。

1. **[ファイル]** メニューから、 **[基本設定]** を選択し、次に **[設定]** を選択します。
1. **[拡張機能]** の下にある **[Notebook 構成]** までスクロールします。
1. **[Use Existing Python]\(既存の Python の使用\)** で、[Local path to a preexisting python installation used by Notebooks]\(Notebooks で使用する既存の Python インストールのローカル パス\) オプションをオフにします。
1. Azure Data Studio を再起動します。

**[ノートブック用 Python の構成]** ページが表示されたら、新しい Python インストールを作成するか、既存のインストールへのパスを指定するかを選択できます。

## <a name="next-steps"></a>次のステップ

Azure Data Studio の SQL ノードブックの詳細については、「[SQL Server 2019 でノートブックを使用する方法](notebooks-guidance.md)」を参照してください。
