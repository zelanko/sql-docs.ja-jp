---
title: DLL をトレース |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- trace DLLs [ODBC]
- tracing options [ODBC], trace DLLs
ms.assetid: 5ab99bd3-cdc3-4e2c-8827-932d1fcb6e00
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ad14958f2dc3967fe8bc041c8144f932b99ec5a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="trace-dll"></a>トレース DLL
トレースを実行する DLL は、ODBC コア コンポーネントのいずれかです。 以前、DLL、Windows SDK のコンポーネントの ODBC サンプル DLL として提供されています、トレースには、Microsoft Data Access Components (MDAC) SDK が含まれています。 したがって、レジストリ エントリ、インターフェイス、およびトレース DLL のサンプル コードは使用できます。 この DLL は、トレースを ODBC ユーザーまたはサード パーティ ベンダーによって生成された DLL で置換できます。 カスタム トレース DLL は、元のサンプル トレース DLL とは異なる名前を指定してください。 システム ディレクトリのトレースの Dll をインストールする必要があります。 または読み込みが失敗します。 接続文字列は渡されません DLL は、トレース、ドライバー マネージャーでします。  
  
 トレースの DLL は、入力引数、出力引数、引数の遅延、リターン コード、および SQLSTATEs をトレースします。 ドライバー マネージャーが 2 つの時点でトレース DLL を呼び出すトレースを有効にすると、: (引数の検証) の前に関数の開始時に 1 回し、もう一度だけ前に、この関数を返します。  
  
 アプリケーションが関数を呼び出すときに、ドライバー マネージャーは、トレース、ドライバーで、関数の呼び出しまたは呼び出し自体を処理する前に DLL にトレース関数を呼び出します。 各 ODBC 関数が、対応するトレース関数 (付いて*トレース*) を除き、名前の ODBC 関数と同じです。 トレース関数が呼び出されると、トレース DLL は入力引数をキャプチャし、リターン コードを返します。 トレースの DLL が呼び出されるため、ドライバー マネージャーが引数を検証する前に、無効な関数の呼び出しは追跡されます、ため、状態遷移のエラーと無効な引数がログに記録されます。  
  
 DLL のトレースにトレース関数を呼び出した後は、ドライバー マネージャーは、ドライバーの ODBC 関数を呼び出します。 呼び出して**TraceReturn**トレース DLL にします。 この関数は 2 つの引数を受け取ります。 トレース関数では、トレース DLL によって返される値と関数の ODBC ドライバー マネージャーに、ドライバーによって返されるリターン コード (または関数を処理する場合、ドライバー マネージャーによってそれ自体が返される値)。 関数では、トレース関数の戻り値を使用して、キャプチャ対象の入力引数の値を操作します。 これは、ログ ファイルに、ODBC 関数の返されたコードを書き込みます (またはが有効になっている場合、動的に表示されます)。 出力引数へのポインターを逆参照し、出力引数値は、ログに記録します。
