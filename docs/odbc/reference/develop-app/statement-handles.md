---
title: ステートメントハンドル |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 730ead7bf90af3b6e6906fe184e0fa3312212137
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107257"
---
# <a name="statement-handles"></a>ステートメント ハンドル
*ステートメント*は、"**従業員から選択\* **" などの SQL ステートメントとして最も簡単に考えることができます。 ただし、ステートメントは SQL ステートメントだけではなく、ステートメントの実行時に使用されるステートメントやパラメーターによって作成された結果セットなど、その SQL ステートメントに関連付けられているすべての情報で構成されます。 ステートメントには、アプリケーション定義の SQL ステートメントも必要ありません。 たとえば、ステートメントで**Sqltables**などのカタログ関数が実行されると、テーブル名のリストを返す定義済みの SQL ステートメントが実行されます。  
  
 各ステートメントは、ステートメントハンドルによって識別されます。 ステートメントは単一の接続に関連付けられており、その接続には複数のステートメントが存在する場合があります。 一部のドライバーでは、サポートするアクティブなステートメントの数が制限されています。**SQLGetInfo**の SQL_MAX_CONCURRENT_ACTIVITIES オプションは、1つの接続でドライバーがサポートするアクティブなステートメントの数を指定します。 ステートメントは、結果が保留になっている場合に*アクティブ*になるように定義されています。結果には、結果セットまたは**INSERT**、 **UPDATE**、または**DELETE**ステートメントの影響を受ける行の数が含まれます。または、複数の呼び出しで**sqlputdata**を使用してデータが送信されます。  
  
 ODBC (ドライバーマネージャーまたはドライバー) を実装するコード内では、ステートメントハンドルによって、ステートメント情報を含む構造体が識別されます。次に例を示します。  
  
-   ステートメントの状態  
  
-   現在のステートメントレベルの診断  
  
-   ステートメントのパラメーターと結果セットの列にバインドされているアプリケーション変数のアドレス  
  
-   各ステートメント属性の現在の設定  
  
 ステートメントハンドルは、ほとんどの ODBC 関数で使用されます。 特に、これらの関数では、パラメーターと結果セットの列 (**SQLBindParameter**および**SQLBindCol**) のバインド、ステートメントの準備と実行 (**SQLPrepare**、 **sqlexecute**、および**SQLExecDirect**)、メタデータの取得 (**Sqlcolattribute**と**SQLDescribeCol**)、フェッチ結果 (**sqlexecute**)、および診断の取得 (**SQLGetDiagField**および**SQLGetDiagRec**) を使用しています。 また、カタログ関数 (**Sqlcolumns**、 **sqlcolumns**など) とその他の多くの関数でも使用されます。  
  
 ステートメントハンドルは**SQLAllocHandle**で割り当てられ、 **sqlfreehandle**で解放されます。
