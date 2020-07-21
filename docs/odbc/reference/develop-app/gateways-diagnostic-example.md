---
title: ゲートウェイ診断の例 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b18fd78be7be2eb79316339cbdf3d315deb194fb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305573"
---
# <a name="gateways-diagnostic-example"></a>ゲートウェイ診断の例
ゲートウェイアーキテクチャでは、ドライバーは ODBC をサポートするゲートウェイに要求を送信します。 ゲートウェイは、要求を DBMS に送信します。 ドライバーマネージャーとのインターフェイスを持つコンポーネントであるため、ドライバーは**SQLGetDiagRec**の引数を書式設定して返します。  
  
 たとえば、Oracle ベースのゲートウェイを使用して Microsoft Open を Data Services、Rdb がテーブル EMPLOYEE を見つけられなかった場合、ゲートウェイは次のような診断メッセージを生成することがあります。  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 データソースでエラーが発生したため、ゲートウェイによって、データソース識別子 ([Rdb]) のプレフィックスが診断メッセージに追加されました。 ゲートウェイはデータソースとの通信を行うコンポーネントであったので、そのベンダー ([DEC]) のプレフィックスと識別子 ([ODS Gateway]) が診断メッセージに追加されました。 また、診断メッセージの先頭に SQLSTATE 値と Rdb エラーコードが追加されました。 これにより、独自のメッセージ構造のセマンティクスを保持しながら、ODBC 診断情報をドライバーに渡すことができます。 ドライバーは、ゲートウェイによってエラーステートメントに関連付けられているエラー情報を解析します。  
  
 ゲートウェイドライバーは、ドライバーマネージャーとのインターフェイスを持つコンポーネントであるため、上記の診断メッセージを使用して書式設定し、 **SQLGetDiagRec**から次の値を返します。  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
