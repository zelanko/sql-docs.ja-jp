---
title: ブロックカーソル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 1a92b5d8-7c6e-4ce5-8c99-600a387026aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa35888ef93da9648fe6422bdc35ebf9da3a0525
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306353"
---
# <a name="block-cursors"></a>ブロック カーソル
多くのアプリケーションは、ネットワークを介してデータを取得するためにかなりの時間を費やしています。 この時間の一部は、実際にはネットワーク経由でデータを取得するのに費やされ、その一部は、データの行を要求するドライバーによって行われる呼び出しなどのネットワーク オーバーヘッドに費やされます。 アプリケーションが*ブロックカーソルまたは**ファット**カーソル*を効率的に使用し、一度に複数の行を返すことができる場合、後者の時間を短縮できます。  
  
 アプリケーションには、常にブロックカーソルを使用するオプションがあります。 一度に 1 行しかフェッチできないデータ ソースでは、ブロック カーソルをドライバーでシミュレートする必要があります。 これは、複数の単一行フェッチを実行することによって行うことができます。 これはパフォーマンスの向上を実現する可能性は低いですが、アプリケーションの機会を開きます。 このようなアプリケーションは、DBMS がブロック カーソルをネイティブに実装し、それらの DBMS に関連付けられているドライバーがそれらを公開する際にパフォーマンスが向上します。  
  
 ブロック カーソルを使用して 1 回のフェッチで返される行は *、rowset*と呼ばれます。 行セットと結果セットを混同しないことが重要です。 結果セットはデータ ソースで維持され、行セットはアプリケーション バッファに保持されます。 結果セットが固定されている間は、行セットは変更されません - 新しい行セットがフェッチされるたびに位置と内容が変更されます。 従来の SQL 順方向専用カーソルのような単一行カーソルが現在の行を指すように、ブロックカーソルは行セットを指し、*これは現在の行*と考えることができます。  
  
 複数の行がフェッチされた場合に 1 つの行に対して操作を実行するには、アプリケーションはまず、どの行が現在の行かを示す必要があります。 現在の行は **、SQLGetData**および位置指定更新ステートメントおよび削除ステートメントの呼び出しによって必要とされます。 ブロック カーソルが最初に行セットを返す場合、現在の行は行セットの最初の行になります。 現在の行を変更するには、アプリケーションは**SQLSetPos**または**SQLBulkOperations** (ブックマークで更新) を呼び出します。 次の図は、結果セット、行セット、現在の行、行セット カーソル、およびブロック カーソルの関係を示しています。 詳細については、このセクションの「[ブロック カーソルの使用](../../../odbc/reference/develop-app/using-block-cursors.md)」および「 SQLSetPos を使用した[位置指定更新とステートメントの削除](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)」および「[データの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)」を参照してください。  
  
 ![次、前、最初、および最後の行セットのフェッチ](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 カーソルがブロック カーソルであるかどうかは、スクロール可能かどうかに依存しません。 たとえば、レポート アプリケーションの作業の大部分は、行の取得と印刷に費やされます。 このため、前方専用のブロック カーソルで最も高速に動作します。 これは、前方スクロール カーソルを使用してスクロール可能なカーソルのコストを回避し、ブロック カーソルを使用してネットワーク トラフィックを削減します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ブロック カーソルで使用するためのバインディング列](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [ブロック カーソルの使用](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [行の状態の配列](../../../odbc/reference/develop-app/row-status-array.md)
