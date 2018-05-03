---
title: 図形の正式な文法 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4283d1858c18cd71e3128df9d58017d2a24cf977
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="formal-shape-grammar"></a>図形の正式な文法
これは、正式な文法任意図形のコマンドを作成するためです。  
  
-   必要な文法的な用語では、山かっこ ("<>") で区切られたテキスト文字列を示します。  
  
-   省略可能な条件は、角かっこ ("") で区切られます。  
  
-   代替手段は、縦棒で示されます ("&#124;") です。  
  
-   繰り返しの代替手段は、省略記号 ([...]) によって示されます。  
  
-   *アルファ*英文字の文字列を示します。  
  
-   *桁*数値の文字列を示します。  
  
-   *Unicode 桁*unicode の数字の文字列を示します。  
  
 その他のすべての用語は、リテラルを示します。  
  
|項目|定義|  
|----------|----------------|  
|\<shape-command>|SHAPE [\<table-exp> [[AS] \<alias>]][\<shape-action>]|  
|\<table-exp>|{\<プロバイダー コマンド テキスト >} &#124; です。<br /><br /> (\<shape コマンド >) &#124;<br /><br /> テーブル\<引用符で囲まれた名 > &#124; です。<br /><br /> \<quoted-name>|  
|\<shape-action>|APPEND\<エイリアス フィールド リスト > &#124; です。<br /><br /> コンピューティング\<エイリアス > [BY\<フィールド リスト >]|  
|\<aliased-field-list>|\<aliased-field> [, \<aliased-field...>]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<関係 exp >) &#124;<br /><br /> \<計算 exp > &#124; です。<br /><br /> \<集計 exp > &#124; です。<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> RELATE \<relation-cond-list>|  
|\<relation-cond-list>|\<relation-cond> [, \<relation-cond>...]|  
|\<relation-cond>|\<フィールド名 > に\<子 ref >|  
|\<child-ref>|\<フィールド名 > &#124; です。<br /><br /> PARAMETER \<param-ref>|  
|\<param-ref>|\<number>|  
|\<field-list>|\<field-name> [, \<field-name>]|  
|\<aggregate-exp>|SUM (\<修飾されたフィールド名 >) &#124;<br /><br /> AVG (\<修飾されたフィールド名 >) &#124;<br /><br /> MIN (\<修飾されたフィールド名 >) &#124;<br /><br /> MAX (\<修飾されたフィールド名 >) &#124;<br /><br /> カウント (\<修飾されたエイリアス > &#124; です。\<修飾名 >) &#124;<br /><br /> STDEV (\<修飾されたフィールド名 >) &#124;<br /><br /> ANY(\<qualified-field-name>)|  
|\<calculated-exp>|CALC(\<expression>)|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<エイリアス >|\<quoted-name>|  
|\<field-name>|\<quoted-name> [[AS] \<alias>]|  
|\<quoted-name>|"\<文字列 >"&#124; です。<br /><br /> '\<文字列 >' &#124;<br /><br /> [\<文字列 >] &#124; です。<br /><br /> \<name>|  
|\<qualified-name>|エイリアス [.alias...]|  
|\<name>|アルファ [alpha &#124; 数字 &#124; 以外の場合は _ &#124; # &#124; : &#124;...]|  
|\<number>|[数字] の数字|  
|\<new-exp>|NEW \<field-type> [(\<number> [, \<number>])]|  
|\<field-type>|OLE DB または ADO データ型です。|  
|\<string>|unicode char [unicode 文字...]|  
|\<expression>|アプリケーションの式のオペランドが同じ行の場合は、他の非計算列用の Visual Basic の場合。|  
  
## <a name="see-also"></a>参照  
 [階層のレコード セット内の行にアクセスします。](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [データ シェイプの概要](../../../ado/guide/data/data-shaping-overview.md)   
 [データ シェイプに必要なプロバイダー](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [図形の APPEND 句](../../../ado/guide/data/shape-append-clause.md)   
 [一般的な図形コマンド](../../../ado/guide/data/shape-commands-in-general.md)   
 [図形の COMPUTE 句](../../../ado/guide/data/shape-compute-clause.md)   
 [Visual Basic for Applications の関数](../../../ado/guide/data/visual-basic-for-applications-functions.md)
