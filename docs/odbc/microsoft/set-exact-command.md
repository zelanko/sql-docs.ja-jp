---
title: 正確なコマンドを設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXACT command [ODBC]
ms.assetid: 9533d3e0-e7c1-49de-a3a3-0cc4373a91cb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e754fff35b6b948ac63d19361067b2d65a07fdd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300872"
---
# <a name="set-exact-command"></a>SET EXACT コマンド
長さが異なる 2 つの文字列を比較するための規則を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 文字が等価となるには、式が文字と一致する必要があることを指定します。 式の末尾ブランクは比較のために無視されます。 比較のために、2 つの式の短い方が、長い式の長さに合わせて右側にブランクが埋め込まれます。  
  
 OFF  
 (デフォルト)。式が同等であるためには、右側の式の末尾に達するまで、文字の文字と一致する必要があることを指定します。  
  
## <a name="remarks"></a>解説  
 両方の文字列が同じ長さである場合、SET EXACT 設定は無効です。  
  
## <a name="string-comparisons"></a>文字列比較  
 Visual FoxPro には、等価性をテストする 2 つの関係演算子があります。  
  
 = 演算子は、同じ型の 2 つの値の比較を実行します。 この演算子は、文字、数値、日付、および論理データの比較に適しています。  
  
 ただし、= 演算子で文字式を比較すると、結果が期待どおりでない場合があります。 文字式は、左から右の文字の文字を比較し、式の一方が他方の式と等しくないか、= 演算子の右側の式の末尾に達するまで (SET EXACT OFF)、または両方の式の終わりに達するまで (SET EXACT ON)。  
  
 == 演算子は、文字データの正確な比較が必要な場合に使用できます。 2 つの文字式を == 演算子と比較する場合、== 演算子の両側の式は、等しいと見なされるためには、ブランクを含むまったく同じ文字を含んでいなければなりません。 == を使用して文字列を比較する場合、SET EXACT 設定は無視されます。  
  
 次の表は、演算子の選択と SET EXACT 設定が比較に与える影響を示しています。 (アンダースコアは空白を表します。  
  
|比較|= 正確なオフ|= 正確なオン|== 正確なオン/オフ|  
|----------------|------------------|-----------------|--------------------------|  
|"abc" = "abc"|一致する|一致する|一致する|  
|"ab" = "abc"|一致なし。|一致なし。|一致なし。|  
|"abc" = "ab"|一致する|一致なし。|一致なし。|  
|"abc" = "ab_"|一致なし。|一致なし。|一致なし。|  
|"ab" = "ab_"|一致なし。|一致する|一致なし。|  
|"ab_" = "ab"|一致する|一致する|一致なし。|  
|"" = "ab"|一致なし。|一致なし。|一致なし。|  
|"ab" = ""|一致する|一致なし。|一致なし。|  
|"__" = ""|一致する|一致する|一致なし。|  
|"" = "___"|一致なし。|一致する|一致なし。|  
|トリム("__") = ""|一致する|一致する|一致する|  
|"" = トリム("__")|一致する|一致する|一致する|  
  
## <a name="see-also"></a>参照  
 [SET ANSI コマンド](../../odbc/microsoft/set-ansi-command.md)
