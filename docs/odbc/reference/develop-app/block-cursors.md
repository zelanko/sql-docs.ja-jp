---
title: "ブロック カーソル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 1a92b5d8-7c6e-4ce5-8c99-600a387026aa
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7747f421fe4a7356086cf27ecf62739f34acdd17
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="block-cursors"></a>ブロック カーソル
多くのアプリケーションでは、かなりのネットワーク経由でデータを取り込む時間が短縮されます。 この時間の部分は実際には、ネットワーク経由でデータを取り込むに費やされたし、1 行のデータを要求する、ドライバーによって行われた呼び出しなどの一部がネットワーク オーバーヘッドで消費されします。 アプリケーションにより効率的に使用する場合、後者の時間を短縮できます。*ブロック、*または*fat、* *カーソル、*を一度に 1 つ以上の行を返すことができます。  
  
 常にアプリケーションでは、ブロック カーソルを使用するオプションがあります。 一度に 1 つだけの行をフェッチできる、データ ソースには、ドライバーでブロック カーソルをシミュレートする必要があります。 これは、複数の単一行のフェッチを実行することによって実行できます。 とはいえ、これは、パフォーマンスが向上する可能性がないアプリケーション用の営業案件を開きます。 このようなアプリケーションでは、Dbms がネイティブ ブロック カーソルを実装し、それらの Dbms に関連付けられているドライバーを公開すると、パフォーマンス向上が、発生します。  
  
 ブロック カーソルを 1 回のフェッチで返される行と呼ばれる、*行セット*です。 これが、結果セットの行セットを混同しないように重要です。 アプリケーションのバッファーに行セットを保持したまま、データ ソースで、結果セットが保持されます。 結果セットを固定すると、行セットではありません: 位置を変更し、内容を一連の行がフェッチされるたびにします。 ブロック カーソルと見なすことができますが、行セットを指す、単一行には、現在の行には、従来の SQL 順方向専用カーソル ポイントなどのカーソルが、同様*現在行*です。  
  
 を実行する操作の操作の単一行の複数の行がフェッチされるときに、アプリケーションが、現在の行の行を最初にことを示す必要があります。 呼び出しによって、現在の行が必要な**SQLGetData**更新を配置し、ステートメントを削除します。 ブロック カーソルは、まず、行セットを返す、ときに、現在の行は、行セットの最初の行がします。 現在の行では、アプリケーションの呼び出しを変更する**SQLSetPos**または**SQLBulkOperations** (をブックマークによる更新) します。 次の図は、結果セット、行セット、現在の行、行セットのカーソル、およびブロック カーソルとの関係を示します。 詳細については、次を参照してください。[ブロック カーソルを使用して](../../../odbc/reference/develop-app/using-block-cursors.md)、このセクションの後と[位置指定の Update ステートメントとステートメントの削除](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)と[SQLSetPos でのデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)です。  
  
 ![次に、前に、最初と最後の行セットのフェッチ](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 カーソルは、ブロック カーソルであるかどうかは、スクロール可能かどうかを依存しません。 たとえば、ほとんどのレポート アプリケーションで作業は取得にかかった時間の行を印刷します。 このため、これが最速が順方向専用をブロック カーソル。 順方向専用カーソルを使用して、スクロール可能なカーソルとネットワーク トラフィックを削減するためのブロック カーソルの費用を回避します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ブロック カーソルで使用するための列のバインド](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [ブロック カーソルを使用します。](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [行の状態配列](../../../odbc/reference/develop-app/row-status-array.md)

