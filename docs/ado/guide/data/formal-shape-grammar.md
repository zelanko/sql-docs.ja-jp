---
title: 仮形の文法 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91bdf0cfbfe87075d2c9484bca7edd835a950ee6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925346"
---
# <a name="formal-shape-grammar"></a>Shape の正式文法
これは、任意のシェイプコマンドを作成するための正式な文法です。  
  
-   必須の文法用語は、山かっこ ("<>") で区切られたテキスト文字列です。  
  
-   省略可能な語句は、角かっこ ("[]") で区切られます。  
  
-   代替手段は、"&#124;" によって示されます。  
  
-   代替の繰り返しは、省略記号 ("...") で示されます。  
  
-   *Alpha*は、アルファベットの文字列を示します。  
  
-   *数字*は、数字の文字列を示します。  
  
-   *Unicode*数字は、unicode の数字の文字列を示します。  
  
 それ以外のすべての用語はリテラルです。  
  
|期間|定義|  
|----------|----------------|  
|\<shape-command>|SHAPE [\<テーブル-exp> [[AS] \<エイリアス>]] [\<図形-アクション>]|  
|\<テーブル-exp>|{\<provider-command text>} &#124;<br /><br /> (\<shape-command>) &#124;<br /><br /> 引用符\<で囲まれたテーブル名の> &#124;<br /><br /> \<引用符で囲まれた名前>|  
|\<図形-アクション>|別名\<フィールドリスト> &#124; の追加<br /><br /> [ \<フィールドリスト> でエイリアス化される\<フィールドリスト> を計算する]|  
|\<別名フィールドリスト>|\<別名フィールド> [、 \<別名フィールド... >]|  
|\<別名フィールド>|\<フィールド-exp> [[AS] \<エイリアス>]|  
|\<フィールド-exp>|(\<リレーションシップ-exp>) &#124;<br /><br /> \<計算済み-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<新規-exp>|  
|<relation_exp>|\<テーブル-exp> [[AS] \<エイリアス>]<br /><br /> リレーションシップ\<の関連付け-リスト>|  
|\<リレーション-リスト>|\<リレーションシップ-> [、 \<関係-同一>...]|  
|\<リレーション-同一>|\<フィールド名> \<子の参照>|  
|\<子参照>|\<フィールド名> &#124;<br /><br /> パラメーター \<param-ref>|  
|\<param-ref>|\<数値>|  
|\<フィールド一覧>|\<フィールド名> [, \<フィールド名>]|  
|\<aggregate-exp>|SUM (\<修飾フィールド名>) &#124;<br /><br /> AVG (\<限定フィールド名>) &#124;<br /><br /> 最小値\<(修飾フィールド名>) &#124;<br /><br /> MAX (\<修飾フィールド名>) &#124;<br /><br /> COUNT (\<修飾エイリアス> &#124; \<修飾名>) &#124;<br /><br /> STDEV (\<修飾フィールド名>) &#124;<br /><br /> ANY (\<修飾フィールド名>)|  
|\<計算済み-exp>|CALC (\<式>)|  
|\<修飾フィールド名>|\<エイリアス>。[\<別名>...]\<フィールド名>|  
|\<エイリアス>|\<引用符で囲まれた名前>|  
|\<フィールド名>|\<引用符で囲まれた名前> [ \<[AS] エイリアス>]|  
|\<引用符で囲まれた名前>|"\<文字列>" &#124;<br /><br /> '\<string> ' &#124;<br /><br /> [\<文字列>] &#124;<br /><br /> \<名前>|  
|\<修飾名>|エイリアス [. alias...]|  
|\<名前>|alpha [α &#124; digit &#124; _ &#124; # &#124;: &#124;...]|  
|\<数値>|数字 [digit...]|  
|\<新規-exp>|新しい\<フィールドの種類> [(\<number> [, \<number>])]|  
|\<フィールド型の>|OLE DB または ADO データ型。|  
|\<文字列>|unicode-char [unicode-char...]|  
|\<式の>|同じ行の他の非計算列であるオペランドを持つ Visual Basic for Applications 式。|  
  
## <a name="see-also"></a>参照  
 [階層レコードセット内の行へのアクセス](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [データシェイプの概要](../../../ado/guide/data/data-shaping-overview.md)   
 [データシェイプに必要なプロバイダー](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape APPEND 句](../../../ado/guide/data/shape-append-clause.md)   
 [一般的なシェイプコマンド](../../../ado/guide/data/shape-commands-in-general.md)   
 [Shape COMPUTE 句](../../../ado/guide/data/shape-compute-clause.md)   
 [Visual Basic for Applications の関数](../../../ado/guide/data/visual-basic-for-applications-functions.md)
