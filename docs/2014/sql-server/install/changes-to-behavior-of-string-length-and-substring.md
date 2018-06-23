---
title: String-length および substring の動作の変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3bdc5e23a18b1b182703a1773dc8476eda8d4b14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165519"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>string-length および substring の動作の変更
  [String-length 関数&#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length)と[substring 関数&#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring)関数が含まれている XML データベースで使用すると、異なる結果を返す可能性がありますサロゲート文字。  
  
## <a name="description"></a>説明  
 ときに、データベースに設定されていると互換性がある[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の動作、 [string-length 関数&#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length)と[substring 関数&#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring)Unicode 補助文字を処理する場合の関数の変更。 U+FFFF より大きいコード ポイントで定義された各 Unicode 補助文字は、これらの関数では 1 文字としてカウントされます。前のバージョンでは 2 文字としてカウントされていました。  
  
 サロゲート文字の詳細については、次を参照してください。[サロゲートおよび補助文字](http://go.microsoft.com/fwlink/?LinkId=178317)です。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
