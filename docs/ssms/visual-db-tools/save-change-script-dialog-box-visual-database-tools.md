---
title: '[変更スクリプトの保存] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7433cef58b79cda782bc5416aafb4c981608c44
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "42776114"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>[変更スクリプトの保存] ダイアログ ボックス (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
このダイアログ ボックスには、最後にテーブルを保存してから、変更を行った [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトが表示されます。 選択した場所に、テキスト ファイル形式でスクリプトを保存することもできます。  
  
テーブル デザイナーのテーブルへの変更を保存しなかった場合に、このダイアログ ボックスにアクセスできます。 **[テーブル デザイナー]** メニューの **[変更スクリプトの生成]** をクリックします。  
  
> [!NOTE]  
> Visual Database Tools によって提供される変更スクリプトにはエラー処理は含まれていません。 ツールが開いた後でデータベース オブジェクトが変更されていないことを前提としているため、変換関連の問題が発生することを想定していません。 変更スクリプトを実行する前に、適切なエラー処理ステートメントを含める必要があります。  
  
## <a name="options"></a>[変数]  
**[保存時に変更スクリプトを自動作成する]**  
オンにすると、テーブルへの変更を保存するときに毎回 **[変更スクリプトの保存]** ダイアログ ボックスが表示されるようになります。  
  
**はい**  
テキスト ファイルの場所を選択できる **[上書き保存]** ダイアログ ボックスを呼び出します。  
  
**いいえ**  
変更スクリプトの作成を取り消します。  
  
