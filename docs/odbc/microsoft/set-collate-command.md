---
title: 照合コマンドの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set collate command [ODBC]
ms.assetid: 00efbcd4-fea8-4061-86a5-82de413cb753
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a9c1dfd59c00ad0ac0b7bd8b8f1cdfccc84d9b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300892"
---
# <a name="set-collate-command"></a>SET COLLATE コマンド
後続のインデックス作成および並べ替え操作での文字フィールドの照合順序を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET COLLATE TO cSequenceName  
```  
  
## <a name="arguments"></a>引数  
 *を指定します。*  
 照合順序を指定します。 次の表に、使用可能な照合順序のオプションについて説明します。  
  
|Options|Language|  
|-------------|--------------|  
|オランダ語|オランダ語|  
|GENERAL|英語、フランス語、ドイツ語、モダンスペイン語、ポルトガル語、その他の西ヨーロッパ言語|  
|ドイツ語|ドイツ語電話帳の注文 (DIN)|  
|アイスランド|アイスランド語|  
|マシン|マシン (以前のバージョンの FoxPro の既定の照合順序)|  
|ノルダン|ノルウェー語, デンマーク語|  
|スペイン語|伝統的なスペイン語|  
|スウェフィン|スウェーデン語, フィンランド語|  
|ユニクト|ユニークな重量|  
  
> [!NOTE]  
>  スペイン語オプションを指定すると *、ch*は*c*と*d*の間でソートされる単一の文字で、 *l*と*m*の間で*並*べ替えます。  
  
 照合順序オプションをリテラル文字列として指定する場合は、必ずオプションを引用符で囲んでください。  
  
```  
SET COLLATE TO "SWEFIN"  
```  
  
 MACHINE は、デフォルトの照合順序オプションであり、Xbase ユーザーが使い慣れているシーケンスです。 文字は、現在のコード ページに表示される順序で並べ替えられます。  
  
 GENERAL は、米国および西ヨーロッパのユーザーに適している可能性があります。 文字は、現在のコード ページに表示される順序で並べ替えられます。 FoxPro バージョン 2.5 より前のバージョンでは、インデックスは、文字フィールドを大文字小文字に変換するために **、UPPER**( ) または**LOWER**( ) 関数を使用して作成されている可能性があります。 FoxPro バージョン 2.5 より新しいバージョンでは、代わりに GENERAL 照合順序オプションを指定し **、UPPER**( ) 変換を省略できます。  
  
 MACHINE 以外の照合順序オプションを指定し、.idx ファイルを作成する場合は、常にコンパクトな .idx が作成されます。  
  
 現在の照合順序を返す場合は、SET("COLLATE") を使用します。  
  
 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)を使用するか[、SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)で接続文字列に Collate キーワードを使用して、データ ソースの照合シーケンスを指定できます。 これは、次のコマンドを発行するのと同じです。  
  
```  
SET COLLATE TO cSequenceName  
```  
  
## <a name="remarks"></a>解説  
 SET COLLATE を使用すると、サポートされている言語のアクセント付き文字を含むテーブルを並べ替えます。 SET COLLATE の設定を変更しても、以前にオープンされたインデックスの照合順序には影響しません。 Visual FoxPro は既存のインデックスを自動的に維持し、同じフィールドに対してもさまざまな種類のインデックスを柔軟に作成できます。  
  
 たとえば、SET COLLATE を GENERAL に設定してインデックスを作成し、後で SET COLLATE 設定をスペイン語に変更した場合、インデックスは GENERAL 照合順序を保持します。  
  
## <a name="see-also"></a>参照  
 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
