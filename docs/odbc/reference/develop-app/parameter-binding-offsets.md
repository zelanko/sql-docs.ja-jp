---
title: パラメーター バインドのオフセット |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1fd069336a52b0a27ae927880f749c02d2c1d43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998925"
---
# <a name="parameter-binding-offsets"></a>パラメーター バインディングのオフセット
アプリケーションがバインドされたパラメーター バッファーのアドレスおよび対応する長さ/インジケーターにオフセットを追加することを指定できますバッファー アドレスとき**SQLExecDirect**または**SQLExecute**が呼び出されます。 これらの追加の結果は、これらの操作で使用されるアドレスを決定します。  
  
 バインドのオフセットを呼び出さずにバインドを変更するアプリケーションを許可する**SQLBindParameter**以前にバインドされたパラメーター。 呼び出し**SQLBindParameter**パラメーターを再バインドするバッファーのアドレスと長さ/インジケーターのポインターを変更します。 単位のオフセットを再バインドその一方で、単にオフセットを追加、既存のバインドされたパラメーター バッファーのアドレスと長さ/インジケーター バッファーのアドレス。 オフセットを使用している場合、バインドは、アプリケーションのバッファーのレイアウトの「テンプレート」と、アプリケーションは、オフセットを変更することでメモリの異なる領域にこの"template"を移動することができます。 新しいオフセットは、いつでも指定することができは常に最初にバインドされた値に追加します。  
  
 バインドのオフセットを指定するには、アプリケーションは、SQLINTEGER バッファーのアドレスに SQL_ATTR_PARAM_BIND_OFFSET_PTR ステートメント属性を設定します。 アプリケーションが、バインドを使用する関数を呼び出す前に \exchsrvr\mtadata\mtacheck.out のオフセット、このバッファー内のバイト パラメーター バッファーのアドレスも長さ/インジケーター バッファーのアドレスは 0、およびバインドされたパラメーターが、SQL ステートメント内に限り、します。 アドレスとオフセットの合計は、有効なアドレスである必要があります。 (このいずれかまたは両方のオフセットとオフセットを追加するアドレスできますしないことを示します有効な場合は、その合計が有効なアドレスである限り。)  
  
> [!NOTE]  
>  ODBC 2 では、バインディングのオフセットはサポートされていません。*x*ドライバー。
