---
title: カーソル | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- forward-only cursors [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], about cursors
- cursors [ODBC]
- fetches [ODBC], cursors
- result sets [ODBC], fetching
- block cursors [ODBC]
ms.assetid: 0b114352-3c63-4d33-9220-182ede90e4aa
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 569714d6cd523498adddbda26576cf376af15c81
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910957"
---
# <a name="cursors"></a>カーソル
アプリケーションでのデータのフェッチ、*カーソル*です。 カーソルが結果セットを異なる: 結果セットは、特定の検索条件に一致する行のセットをアプリケーションにこれらの行を返すのに対し、カーソルは、ソフトウェア。 名前*カーソル、* データベースに適用される、コンピューターの端末に点滅するカーソルから発生した可能性があります。 そのカーソルは、どこに型指定された単語が [次へ] を表示し、画面上の現在の位置を示すと同様、結果セットのカーソルは結果セットとどのような行が次に返されますの現在の位置を示します。  
  
 ODBC のカーソル モデルは、embedded SQL のカーソル モデルに基づきます。 これらのモデルの 1 つの大きな違いは、方法カーソルが開かれるです。 SQL では埋め込まれた、カーソル必要がある明示的に宣言され、開かを使用する前にします。 ODBC では、結果セットを作成するステートメントが実行されたときにカーソルをオープンに暗黙的にします。 カーソルを開いたときに、結果セットの最初の行の前に位置付けられます。 埋め込まれた SQL と ODBC の両方で、アプリケーションの使用が終了した後、カーソルを閉じる必要があります。  
  
 別のカーソルでは、さまざまな特性があります。 呼び出されるカーソルの最も一般的な種類、*順方向専用カーソルでは、* のみが結果セットに移動します。 前の行に戻り、アプリケーションする必要があります、カーソル閉じてから、必要な行に達するまで、結果セットの先頭から行を読み取る。 順方向専用カーソルでは、結果セットを 1 つのパスを行うための高速なメカニズムを提供します。  
  
 順方向専用カーソルは、小さい画面に基づくアプリケーション、ユーザーが逆方向にスクロールするのに役立ちますデータを転送します。 このようなアプリケーションは、結果セット データをローカルにキャッシュされ、スクロール自体の実行後を参照して、順方向専用カーソルを使用できます。 これは、少量のデータでのみ使用します。 良いソリューションは、使用する、*スクロール可能なカーソルは、* おり、結果セットへのランダム アクセスを提供します。 このようなアプリケーションも、パフォーマンスが向上する時に、データの 1 つ以上の行をフェッチと呼ばれるものを使用して、*カーソルをブロックします。* ブロック カーソルの詳細については、次を参照してください。[ブロック カーソルを使用して](../../../odbc/reference/develop-app/using-block-cursors.md)です。  
  
 順方向専用カーソルは、ODBC の既定のカーソルの種類は、およびについては、次のセクションで説明します。 ブロック カーソルとスクロール可能なカーソルの詳細については、次を参照してください。[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)と[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)です。  
  
> [!IMPORTANT]  
>  コミットまたはロールバック、トランザクションは、明示的に呼び出すか**SQLEndTran**または自動コミット モードで動作して一部のデータ ソース接続ですべてのステートメントでのすべてのカーソルを閉じると発生します。 詳細についてで SQL_CURSOR_COMMIT_BEHAVIOR および SQL_CURSOR_ROLLBACK_BEHAVIOR 属性を参照してください、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。
