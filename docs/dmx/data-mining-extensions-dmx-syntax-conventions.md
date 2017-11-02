---
title: "データ マイニング拡張機能 (DMX) 構文表記規則 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], syntax conventions
- syntax [DMX]
- DMX [Analysis Services], syntax conventions
ms.assetid: 7a885df3-9500-4793-9307-90a7d617f486
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: da471964caa7ceb04fe57d79bcb26ed53530096d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="data-mining-extensions-dmx-syntax-conventions"></a>データ マイニング拡張機能 (DMX) 構文表記規則
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データ マイニング拡張機能 (DMX) のリファレンス ドキュメントを[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] DMX 言語を記述する次の規則を使用します。  
  
|表記|使用方法|  
|----------------|-----------|  
|**太字**|記載されているとおりに入力する必要がある DMX のキーワードおよびテキストを示します。|  
|*斜体*|ユーザーが指定する DMX 構文の引数を示します。|  
|(& a) #124 です。(縦棒)|角かっこ、または中かっこで囲まれた項目を区切るために使用されます。 選択できる項目は 1 つだけです。|  
|`[ ]`(かっこ)|省略可能な構文項目が含まれてください。 角かっこは入力しません。|  
|{} (中かっこ)|必要な構文項目が含まれてください。 中かっこは入力しません。|  
|, ...|コンマの前の項目を、任意の回数繰り返せることを示します。 項目は、コンマで区切られます。|  
|\<ラベル >:: =|構文のブロックの名前を示します。 この表記規則は、1 つのステートメント内の複数の箇所で使用できる長い構文の一部、または構文の 1 単位について、グループ化してラベルを付ける際に使用します。 構文のブロックを使用できる箇所はなど、二重山かっこで囲まれたラベル\<ラベル >。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)  
  
  


