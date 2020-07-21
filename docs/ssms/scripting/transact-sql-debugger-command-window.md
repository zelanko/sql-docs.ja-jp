---
title: '[コマンド] ウィンドウ'
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 226acc4696b5edacde3b6950c10c8b5370e29b42
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75243427"
---
# <a name="transact-sql-debugger---command-window"></a>Transact-SQL デバッガー - [コマンド] ウィンドウ

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**[コマンド]** ウィンドウを使用すると、現在デバッグ中の [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディター ウィンドウのコードに対してデバッグ コマンドや編集コマンドなどのコマンドを実行できます。 **[コマンド]** ウィンドウを使用するには、デバッグ モードである必要があります。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **[コマンド]** ウィンドウでもサポートされているコマンドの多くをサポートしています。 詳細については、 [Visual Studio のコマンド ウィンドウに関するページ](https://go.microsoft.com/fwlink/?LinkId=112007)を参照してください。  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>タスク一覧

**[コマンド] ウィンドウにアクセスするには**

- **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。

**変数の値を出力するには**

- **[コマンド] ウィンドウ**で、「**Debug.Print \<変数名>** 」と入力し、Enter キーを押します。

**現在のスレッドに関する情報を一覧表示するには**

- **[コマンド]** ウィンドウで、「 **Debug.ListThread**」と入力し、Enter キーを押します。

**[クイック ウォッチ] ウィンドウに変数を追加するには**

- **[コマンド] ウィンドウ**で、「**Debug.QuickWatch \<変数名>** 」と入力し、Enter キーを押します。

## <a name="see-also"></a>参照

[Transact-SQL デバッガー](../../relational-databases/scripting/transact-sql-debugger.md)
