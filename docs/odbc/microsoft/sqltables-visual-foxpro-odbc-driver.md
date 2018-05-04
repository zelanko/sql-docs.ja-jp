---
title: SQLTables (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d15e72670bda9c70939cc0b5f0eaa75f855edc7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 内のパラメーターで指定されたテーブル名の一覧を返します、 **SQLTables**ステートメントです。 パラメーターが指定されていない場合は、現在のデータ ソースに格納されているテーブル名を返します。 ドライバーは、情報の結果セットとしてを返します。  
  
 列挙型の呼び出しでは、リモート ビュー、またはローカル パラメーター化されたビューの結果セットのエントリは表示されません。 ただしへの呼び出し**SQLTables**一意テーブルの名前指定子は、一致を見つけるこのようなビューの名前の存在する場合です。 これにより、新しいテーブルを作成する前に名前の競合を確認するために使用する API。  
  
> [!NOTE]  
>  Visual FoxPro ODBC ドライバーが区別[データベース テーブル](../../odbc/microsoft/visual-foxpro-terminology.md)と[テーブルの空き](../../odbc/microsoft/visual-foxpro-terminology.md)テーブルの両方の種類が、システム上の同じディレクトリに格納されている場合でも、します。 データ ソースが、無料のテーブルのディレクトリの場合は、Visual FoxPro ODBC ドライバーはいないカタログまたはデータベースに関連付けられているすべてのテーブルの名前を返します。  
  
 詳細については、次を参照してください。 [SQLTables](../../odbc/reference/syntax/sqltables-function.md)で、 *ODBC プログラマ リファレンス*です。
