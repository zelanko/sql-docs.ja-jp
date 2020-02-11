---
title: Microsoft Access から Visual FoxPro データを照会および更新する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2681ecd0fe6f586954236c4fb5fddcf576b206be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67988061"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Microsoft Access からクエリを実行して Visual FoxPro データを更新する
[テーブルのリンク] オプションを使用して、Microsoft Access データベースから Visual FoxPro データベースに格納されているデータのクエリや更新を行うことができます。  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Visual FoxPro データベースを Microsoft Access データベースにリンクするには  
  
1.  Microsoft Access データベースを開きます。  
  
2.  [テーブル] タブの [新規作成] をクリックします。  
  
3.  [新しいテーブル] ダイアログボックスで、[テーブルのリンク] を選択し、[OK] をクリックします。  
  
4.  [リンク] ダイアログボックスの [ファイルの種類] ボックスの一覧で、[ODBC データベース] を選択します。  
  
5.  [SQL データソース] ダイアログボックスで、クエリを実行する Visual FoxPro データに接続するデータソースを選択し、[OK] をクリックします。  
  
6.  [テーブルのリンク] ダイアログボックスで、クエリおよび更新するテーブルを選択し、[OK] をクリックします。 リンクされた Visual FoxPro テーブルは、Microsoft Access データベースの [テーブル] タブに表示されます。  
  
 これで、Microsoft Access を使用して、リンクされた Visual FoxPro テーブルのデータに対してクエリおよび更新を実行できるようになりました。 リンクデータに対して行った変更は、Visual FoxPro データソースに送り返されます。  
  
 Microsoft Access で行った変更が Visual FoxPro データソースのデータに影響しないようにする場合は、「 [Microsoft access への Visual Foxpro データのインポート](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md)」を参照してください。
