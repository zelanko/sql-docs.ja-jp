---
title: "SET COLLATE コマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- set collate command [ODBC]
ms.assetid: 00efbcd4-fea8-4061-86a5-82de413cb753
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dfd2225157c048840cd20bd140ed74ae31384b8a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="set-collate-command"></a>SET COLLATE コマンド
後続のインデックス作成と並べ替え操作では、文字列フィールドの照合順序を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET COLLATE TO cSequenceName  
```  
  
## <a name="arguments"></a>引数  
 *cSequenceName*  
 照合順序を指定します。 使用可能な照合シーケンスのオプションは、次の表で説明します。  
  
|オプション|言語|  
|-------------|--------------|  
|オランダ語|オランダ語|  
|GENERAL|英語、フランス語、ドイツ語、最新のスペイン語、ポルトガル語、およびその他の西ヨーロッパ言語|  
|ドイツ語|ドイツ語の電話帳順序 (DIN)|  
|アイスランド|アイスランド語|  
|マシン|コンピューター (FoxPro の以前のバージョンの既定の照合順序)|  
|NORDAN|ノルウェー語、デンマーク語|  
|スペイン語|従来のスペイン語|  
|SWEFIN|スウェーデン語、フィンランド語|  
|UNIQWT|一意の重み|  
  
> [!NOTE]  
>  スペイン語のオプションを指定するときに*ch*間でソートする 1 つの文字は、 *c*と*d*、および*ll*間並べ替えます*l*と*m*です。  
  
 リテラル文字列の照合順序のシーケンスのオプションを指定する場合は、引用符で囲むオプションを必ず。  
  
```  
SET COLLATE TO "SWEFIN"  
```  
  
 コンピューターは既定の照合順序のシーケンスのオプション、シーケンス Xbase ユーザーが慣れています。 現在のコード ページに表示される、文字が並べ替えられています。  
  
 [全般] は、米国とヨーロッパのユーザーに適して可能性があります。 現在のコード ページに表示される、文字が並べ替えられています。 FoxPro バージョン 2.5 より前のインデックス作成されている場合を使用して、**上限**に関するページ () または**低い**文字フィールドを一貫性のあるケースに変換する () 関数です。 FoxPro バージョン 2.5 以降の場合は、代わりに、一般的な照合順序のシーケンス オプションを指定を省略できます、**上限**() 変換します。  
  
 コンピューターおよび .idx ファイルを作成するかどうか以外の照合順序のシーケンス オプションを指定すると、compact .idx が常に作成されます。  
  
 SET("COLLATE") を使用して、現在の照合順序を返します。  
  
 使用して、データ ソースの照合順序を指定することができます、 [ODBC Visual FoxPro 設定 ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)または Collate キーワードを使用、接続文字列でを使用して[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)です。 これは、次のコマンドを実行する同じです。  
  
```  
SET COLLATE TO cSequenceName  
```  
  
## <a name="remarks"></a>解説  
 部単位印刷設定を使用すると、サポートされている言語のいずれかのアクセント記号付き文字を含む注文テーブルにします。 部単位印刷設定の設定を変更すると、既に開かれているインデックスの照合順序に影響しません。 Visual FoxPro 既存のインデックスを自動的に管理をさまざまな種類の同じフィールドに対しても、インデックスを作成する柔軟性を提供することができます。  
  
 たとえば、設定には、[全般] に設定部単位印刷とインデックスの作成し、スペイン語、部単位印刷設定の設定が変更された後で、インデックスには一般的な照合順序が保持されます。  
  
## <a name="see-also"></a>参照  
 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)

