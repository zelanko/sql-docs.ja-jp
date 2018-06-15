---
title: Visual C でのエラー処理 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68ce5fb8cc94b130de5171a45b65743e86eec3da
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271691"
---
# <a name="handling-errors-in-visual-c"></a>Visual C でのエラーを処理
COM では、ほとんどの操作は、関数が正常に完了したかどうかを示す HRESULT のリターン コードを返します。 #Import ディレクティブでは、各「生の」メソッドまたはプロパティの周囲にラッパー コードを生成し、返された HRESULT を確認します。 HRESULT エラーを示している場合、ラッパー コードは、引数として HRESULT のリターン コードの呼び出し元の _com_issue_errorex() によって COM エラーをスローします。 COM エラー オブジェクトをキャッチすることができます、 **try catch**ブロックします。 (効率性のためは、_com_error オブジェクトへの参照をキャッチします)。  
  
 ただし、これらは、ADO エラー: ADO 操作の失敗に起因します。 基になるプロバイダーから返されたエラーとして表示されます**エラー**内のオブジェクト、**接続**オブジェクトの**エラー**コレクション。  
  
 #Import ディレクティブでは、エラー処理ルーチンで、ADO .dll で宣言されたプロパティとメソッドのみを作成します。 ただし、独自のエラー チェック マクロまたはインライン関数を記述するこれと同じエラー処理メカニズムを活用を行うことができます。 例については、C++® Extensions トピックを参照してください。
