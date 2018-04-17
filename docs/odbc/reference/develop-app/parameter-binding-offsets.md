---
title: パラメーター バインドのオフセット |Microsoft ドキュメント
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
- offsets of parameters [ODBC]
- binding offsets of parameters [ODBC]
ms.assetid: 309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d5228c7ce920eb56b0b947784b3d5a7bb2d6266
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-binding-offsets"></a>パラメーターのバインドのオフセット
アプリケーションでは、バインドされたパラメーター バッファーのアドレスおよび対応する長さ/インジケーターにオフセットを追加することを指定できるときにバッファー アドレス**SQLExecDirect**または**SQLExecute**と呼びます。 これらの追加の結果では、これらの操作で使用されるアドレスを決定します。  
  
 バインドのオフセットを呼び出さずにバインドを変更するアプリケーションを許可する**SQLBindParameter**以前にバインドされたパラメーターにします。 呼び出し**SQLBindParameter**パラメーターを再バインドするバッファーのアドレスと長さ/インジケーターのポインターを変更します。 オフセットを再バインド一方で、単にオフセットを追加、既存のバインドされたパラメーター バッファーのアドレスと長さ/インジケーター バッファーのアドレス。 オフセットを使用している場合、バインディングは、アプリケーションのバッファーのレイアウトの"template"と、アプリケーションは、オフセットを変更することによってメモリの異なる領域にこの"template"を移動することができます。 新しいオフセットを使用して、いつでもに指定することができますは常に最初にバインドされた値に追加します。  
  
 バインドのオフセットを指定するには、アプリケーションは、SQLINTEGER バッファーのアドレスを SQL_ATTR_PARAM_BIND_OFFSET_PTR ステートメント属性を設定します。 アプリケーションが、バインドを使用する関数を呼び出す前に置きますオフセットこのバッファー内のバイトとしてパラメーター バッファーのアドレスも長さ/インジケーター バッファーのアドレスは、0、および SQL ステートメントでは、バインドされたパラメーター。 アドレスとオフセットの合計は、有効なアドレスである必要があります。 (このいずれかまたは両方オフセットとアドレスのオフセットを追加することができますしないことを示します有効な場合は、その合計が有効なアドレスである限り。)  
  
> [!NOTE]  
>  バインディングのオフセットは、ODBC 2 ではサポートされていません。*x*ドライバー。
