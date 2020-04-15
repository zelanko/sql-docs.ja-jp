---
title: SQL バインドパラメーター (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55708cc5192fb40149d6db7710f6ee638c4880d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305430"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**SQLBindParameter**関数を使用する方法について説明します。 一般的な情報については **、「SQLBindParameter**関数 」を参照[してください](../../../odbc/reference/syntax/sqlbindparameter-function.md)。  
  
 アプリケーションは、バインドされた列の C データ・タイプ、列サイズ、および 10 進数の数字が同じである限り、 **SQLBindParameter**を呼び出してパラメーターを再バインドできます。  
  
 カーソル ライブラリでは、バインド オフセットを使用するSQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の設定がサポートされています。 ( この再バインドを行うために**SQLBindParameter**を呼び出す必要はありません)。  
  
 カーソル ライブラリは、実行時のデータ パラメーターのバインドをサポートします。
