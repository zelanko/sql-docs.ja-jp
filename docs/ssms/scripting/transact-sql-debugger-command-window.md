---
title: '[コマンド] ウィンドウ'
description: Transact-SQL デバッガーの [コマンド] ウィンドウを使用して、デバッグ コマンドを実行したり、デバッグ中のコードのコマンドを編集したりする方法について説明します。
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 983f6d846d1cb9be973c4976798fb55580dc7f2f
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97476803"
---
# <a name="transact-sql-debugger---command-window"></a>Transact-SQL デバッガー - [コマンド] ウィンドウ

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

**[コマンド]** ウィンドウを使用して、現在デバッグ中の [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディター ウィンドウのコードに対して、デバッグ コマンドや編集コマンドなどのコマンドを実行します。 **[コマンド]** ウィンドウを使用するには、デバッグ モードである必要があります。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **[コマンド]** ウィンドウでもサポートされているコマンドの多くをサポートしています。 詳細については、 [Visual Studio のコマンド ウィンドウに関するページ](https://go.microsoft.com/fwlink/?LinkId=112007)を参照してください。  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>タスク一覧

**[コマンド] ウィンドウにアクセスするには**

- **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。

**変数の値を出力するには**

- **[コマンド]** ウィンドウで、「**Debug.Print \<VariableName>** 」と入力し、Enter キーを押します。

**現在のスレッドに関する情報を一覧表示するには**

- **[コマンド]** ウィンドウで、「 **Debug.ListThread**」と入力し、Enter キーを押します。

**[クイック ウォッチ] ウィンドウに変数を追加するには**

- **[コマンド] ウィンドウ** で、「**Debug.QuickWatch \<VariableName>** 」と入力し、Enter キーを押します。

## <a name="see-also"></a>参照

[Transact-SQL デバッガー](../../relational-databases/scripting/transact-sql-debugger.md)
