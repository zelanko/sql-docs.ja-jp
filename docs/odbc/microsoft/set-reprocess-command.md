---
title: 再処理コマンドの SET |Microsoft ドキュメント
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
- SET REPROCESS command [ODBC]
ms.assetid: b0708757-b1d7-42f3-8988-787f2a806b8b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7dbfee063d403605fe2a72efada88ecf0d84e34
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="set-reprocess-command"></a>再処理コマンドのセット
ロック失敗後のファイルまたはレコードのロックに長時間かかる場合または方法の数を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET REPROCESS TO nAttempts [SECONDS] | TO AUTOMATIC  
```  
  
## <a name="arguments"></a>引数  
 *NAttempts*[秒]  
 何回か失敗した最初の試行後に、レコードまたはファイルをロックしようとする秒数を指定します。 既定値は 0 です。最大値は、32,000 です。  
  
 Visual FoxPro がまたはに記録するファイルをロックしようとする秒数を指定*nAttempts* (秒)。 場合にのみ使用が*nAttempts*が 0 より大きい。  
  
 たとえば場合、 *nAttempts* 30、Visual FoxPro がレコードをロックまたはファイルの最大 30 回試行します。 秒 (設定を再処理を 30 秒を含めることも、Visual FoxPro は継続的に最大で 30 秒のレコードまたはファイルをロックする試行します。  
  
 ON エラー ルーチンが有効になっていると、レコードまたはファイルをロックするためのコマンドを試行が成功した場合は、ON エラー ルーチンが実行されます。 ただし、関数は、ロックを試みると、ON エラー ルーチンが実行されない場合は、関数、False を返します (です。F.)。  
  
 ON エラー ルーチンが有効ではありません、コマンドが、レコードまたはファイルをロックしようとしてロックを配置することはできません、エラーが生成されます。 関数は、ロックを配置すると、アラートが表示されていない、関数、False を返します (です。F.)。  
  
 場合*nAttempts* 0 (既定値) が、コマンドまたはレコードまたはファイルをロックしようとする関数を実行して、Visual FoxPro がレコードをロックしたり、ファイルを無期限にします。 レコードまたはファイルには、待機中にロックするために使用できるになると、ロックを配置され、システム メッセージがクリアされます。 関数が、ロックを配置しようとすると場合、関数は True を返します (です。T.)。  
  
 ON エラー ルーチンが有効になり、コマンドがレコードまたはファイルをロックしようとすると場合、は、ON エラー ルーチンが、レコードまたはファイルをロックする追加の試行回数よりも優先されます。 ON エラー ルーチンは、すぐに実行されます。 Visual FoxPro は追加のレコードまたはファイルのロックを行いません、システム メッセージは表示されません。  
  
 場合*nAttempts* 1 は、Visual FoxPro がレコードをロックまたはファイルを無期限にしようとして ON エラー ルーチンが実行されない場合は。  
  
 ロックは、レコードをロックしようとしているファイルに別のユーザーによって設定されているが場合、は、ユーザーがロックを解放するまでを待機する必要があります。  
  
 自動  
 Visual FoxPro レコード ロックまたはバックアップ ファイルを無期限にすることを指定します。 (-2 に設定の再処理とは、同等のコマンドのことです)。  
  
## <a name="remarks"></a>解説  
 レコードまたはファイルをロックする最初の試行は成功は限りません。 多くの場合、レコードまたはファイルは、ネットワーク上の別のユーザーによってロックされています。 設定を再処理すると、Visual FoxPro は、追加の試行を最初の試行が成功すると、レコードまたはファイルをロックするかどうかを判断します。 指定するに何回か追加の試行が行われるまたは時間の試行が行われます。 ON エラー ルーチンでは、試行の処理方法に失敗した場合のロックに影響します。
