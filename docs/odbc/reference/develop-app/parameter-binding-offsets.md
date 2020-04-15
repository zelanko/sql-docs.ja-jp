---
title: パラメータバインドオフセット |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- offsets of parameters [ODBC]
- binding offsets of parameters [ODBC]
ms.assetid: 309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: de67b230883f3cf8a582e73ce82e8c4bd7d21ad0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282496"
---
# <a name="parameter-binding-offsets"></a>パラメーター バインディングのオフセット
アプリケーションは、バインドされたパラメーター バッファー アドレスと **、SQLExecDirect**または**SQLExecute**が呼び出されたときに、対応する長さ/インジケーター バッファー アドレスにオフセットを追加することを指定できます。 これらの追加の結果によって、これらの操作で使用されるアドレスが決まります。  
  
 バインド オフセットを使用すると、アプリケーションは、以前にバインドされたパラメーターの**SQLBindParameter**を呼び出すことなく、バインドを変更できます。 パラメーターを再バインドするための**SQLBindParameter**の呼び出しは、バッファー・アドレスと長さ/インジケーター・ポインターを変更します。 一方、オフセットを使用して再バインドすると、既存のバインドパラメータバッファアドレスと長さ/インジケーターバッファアドレスにオフセットが追加されます。 オフセットを使用する場合、バインドはアプリケーション バッファのレイアウト方法の"テンプレート"であり、アプリケーションはオフセットを変更することでこの "テンプレート" をメモリの別の領域に移動できます。 新しいオフセットはいつでも指定でき、常に元のバインド値に追加されます。  
  
 バインド オフセットを指定するために、アプリケーションは SQL_ATTR_PARAM_BIND_OFFSET_PTR ステートメント属性を SQLINTEGER バッファーのアドレスに設定します。 バインディングを使用する関数をアプリケーションが呼び出す前に、パラメーター バッファー アドレスも長さ/インジケーター バッファー アドレスも 0 で、バインド パラメータが SQL ステートメント内にある限り、このバッファにオフセットをバイト単位で配置します。 アドレスとオフセットの合計は、有効なアドレスである必要があります。 (つまり、オフセットの合計が有効なアドレスである限り、オフセットとオフセットを追加するアドレスのいずれかまたは両方が無効になる可能性があります。  
  
> [!NOTE]  
>  バインド オフセットは ODBC 2 ではサポートされていません。*x*ドライバ。
