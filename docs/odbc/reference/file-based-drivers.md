---
title: ファイル ベースのドライバー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45d9203a08b9c70809e81fb3d9cf84a521017068
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722960"
---
# <a name="file-based-drivers"></a>ファイル ベースのドライバー
ファイル ベースのドライバーがドライバーを使用するためのスタンドアロン データベース エンジンを提供しない dBASE などのデータ ソースで使用されます。 これらのドライバーでは、物理的なデータに直接アクセスし、プロセスの SQL ステートメントをデータベース エンジンを実装する必要があります。 ファイル ベースのドライバーでのデータベース エンジンが、最小 SQL への準拠レベルで定義されている ODBC SQL のサブセットを実装する標準的な方法では、この準拠レベル内の SQL ステートメントの一覧は、[付録 c: SQL の文法](../../odbc/reference/appendixes/appendix-c-sql-grammar.md)を参照してください。  
  
 ファイルおよび DBMS ベースのドライバーを比較する、ファイル ベースのドライバーは、データベース エンジンのコンポーネント、ネットワークの部分がないため、構成する簡単なため作成が難しくと性能の低い数人のユーザーがデータベースに書き込む時間企業のデータベースによって生成されたものと、強力なエンジン。  
  
 次の図は、ネットワーク ファイル サーバー上のファイル ベースのドライバーや、データがローカルに存在する 1 つが存在するその他の 2 つの異なる構成を示します。  
  
 ![2 つの構成ファイルの&#45;ベースのドライバー](../../odbc/reference/media/pr06.gif "pr06")
