---
title: 再処理コマンドの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET REPROCESS command [ODBC]
ms.assetid: b0708757-b1d7-42f3-8988-787f2a806b8b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5a7eb5fd19ca538c4f25077926567011ae133e54
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300832"
---
# <a name="set-reprocess-command"></a>SET REPROCESS コマンド
ロックの試行が失敗した後にファイルまたはレコードをロックする回数またはロック時間を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET REPROCESS TO nAttempts [SECONDS] | TO AUTOMATIC  
```  
  
## <a name="arguments"></a>引数  
 *試行回数 [* 秒]  
 最初に失敗した後にレコードまたはファイルをロックしようとする回数または秒数を指定します。 デフォルト値は 0 です。最大値は 32,000 です。  
  
 秒は、ビジュアルフォックスプロが*nAttempt*秒の間、ファイルまたはレコードをロックすることを指定します。 *nAttempts*が 0 より大きい場合にのみ使用できます。  
  
 たとえば *、nAttempts*が 30 の場合、Visual FoxPro はレコードまたはファイルを 30 回までロックしようとします。 SECONDS (再処理を 30 秒に設定) も含める場合、Visual FoxPro は、最大 30 秒間、レコードまたはファイルをロックしようとします。  
  
 ON ERROR ルーチンが有効であり、レコードまたはファイルをロックするコマンドの試行が失敗した場合は、ON ERROR ルーチンが実行されます。 ただし、関数がロックを試みた場合、ON ERROR ルーチンは実行されず、関数は False (.F.  
  
 ON ERROR ルーチンが有効でない場合、コマンドはレコードまたはファイルをロックしようとし、ロックを配置できない場合は、エラーが生成されます。 関数がロックを設定しようとすると、警告は表示されず、関数は False (.F.  
  
 *nAttempts*が 0 (デフォルト値) の場合、レコードまたはファイルをロックしようとするコマンドまたは関数を発行すると、Visual FoxPro はレコードまたはファイルを無期限にロックしようとします。 待機中にレコードまたはファイルがロック可能になった場合は、ロックが入れられ、システム・メッセージがクリアされます。 関数がロックを設定しようとした場合、関数は True (.T.  
  
 ON ERROR ルーチンが有効であり、コマンドがレコードまたはファイルをロックしようとしている場合、ON ERROR ルーチンは、レコードまたはファイルをロックしようとする追加の試みよりも優先されます。 ON ERROR ルーチンは直ちに実行されます。 Visual FoxPro は追加のレコードまたはファイル ロックを試行せず、システム メッセージを表示しません。  
  
 *nAttempts が*1 の場合、Visual FoxPro はレコードまたはファイルを無期限にロックしようとし、ON ERROR ルーチンは実行されません。  
  
 ロックしようとしているレコードまたはファイルに別のユーザーがロックを設定した場合は、ユーザーがロックを解除するまで待つ必要があります。  
  
 自動に  
 Visual FoxPro がレコードまたはファイルを無期限にロックすることを指定します。 (SET REPROCESS to -2 は同等のコマンドです。  
  
## <a name="remarks"></a>解説  
 レコードまたはファイルをロックする最初の試行は、必ずしも成功するとは限りません。 レコードまたはファイルは、ネットワーク上の別のユーザーによってロックされる場合があります。 SET REPROCESS は、最初の試行が失敗したときに、Visual FoxPro がレコードまたはファイルをロックするために追加の試行を行うかどうかを決定します。 追加の試行回数または試行の実行時間を指定できます。 ON ERROR ルーチンは、失敗したロック試行の処理方法に影響します。
