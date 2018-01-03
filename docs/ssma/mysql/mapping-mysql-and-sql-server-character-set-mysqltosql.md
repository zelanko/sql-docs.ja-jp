---
title: "MySQL および SQL Server の文字のマッピング (MySQLToSQL) を設定 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 20b3f22e-16a2-4a87-b4eb-c277be6bf5c8
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c9b3fc89548b10593cb16e2a70c93afe9b56350e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-mysql-and-sql-server-character-set-mysqltosql"></a>(MySQLToSQL) を設定する MySQL および SQL Server の文字のマッピング
MySQL の文字データ型、式およびリテラルの文字セット (文字セット) を指定できます。  
  
## <a name="charset-mapping"></a>文字セットのマッピング  
文字セットのマッピングが各 MySQL 文字セットを定義し、文字データ型の変換中に使用します。 特定の文字セットの文字の文字列データ型に変換する方法を指定します。  
  
-   SQL Server の各国語文字型 (NCHAR/NVARCHAR) にまたは  
  
-   通常の SQL Server 文字型 (CHAR と VARCHAR)  
  
1.  **各国語**ターゲット データベースの文字データ型は。  
  
    1.  **nchar**  
  
    2.  **nvarchar**  
  
2.  **正規**ターゲット データベースの文字データ型は。  
  
    1.  **char**  
  
    2.  **varchar**  
  
3.  型のマッピングへのマッピングのみが許可**national**文字データ型。 型マッピングに従って MySQL 文字データ型を変換すると、文字セットのマッピングが適用されます。  
  
> [!NOTE]  
> 文字セット マッピングでは、メタデータ オブジェクト エクスプ ローラーのノードの各レベルで定義されていることができます、MySQL から読み取られたすべての文字セットを表します。  
  
## <a name="charset-mapping-on-different-node-levels"></a>文字セットが別のノード レベルのマッピング  
文字セットのマッピングは異なります、別のノード レベルでつまり。  
  
1.  ルート ノードのメタデータ レベル上  
  
2.  データベース、カテゴリとオブジェクトのノードのレベル  
  
> [!NOTE]  
> 文字セットのマッピングを編集用に選択 タブには、別のノード レベルでのマッピングに関係なく、3 つのボタンが含まれています。  
>   
> これらは次のとおりです。  
>   
> 1.  **適用されます。** charset マッピングの編集と保存されていない場合にのみ有効になっている、ユーザーによって行われた変更を適用します。  
> 2.  **[キャンセル]:**ユーザーによって行われた変更を取り消します。 ボタンは、文字セットのマッピングの編集が保存されない場合に有効に取得します。  
> 3.  **既定値にリセット:**すべてのマッピングを既定値にリセットします。  
  
1.  **ルート メタデータ ノード レベル:** Charset マッピング グリッドには、列は、各文字セットを別の文字セットのグリッドが含まれています。 グリッドの列は次のとおりです。  
  
    1.  という名前のグリッドの最初の列**文字セットの名前**文字セットの名前が含まれています。  
  
    2.  という 2 つ目**Charset 説明**文字セットの説明が含まれています。  
  
    3.  3 番目の列のタイトル、**ターゲット文字セットの種類**特定の文字セットのマッピングの設定が含まれています。 この列の値は次のとおりです。  
  
        -   CHAR と VARCHAR  
  
        -   NCHAR/NVARCHAR  
  
    > [!IMPORTANT]  
    > 特定の文字セットの既定値では、CHAR/VARCHAR、NCHAR/NVARCHAR または後に、プレフィックス '(既定値)' があります。  
  
    MySQL データベースとメタデータのルート ノード レベルでターゲット データベースの間で文字セットのマッピングは次のとおりです。  
  
    ||||  
    |-|-|-|  
    |**文字セットの名前**|**文字セットの説明**|**ターゲット文字セットの種類 (既定値)**|  
    |big5|Big5 繁体字中国語|NCHAR と NVARCHAR (既定値)|  
    |dec8|DEC 西ヨーロッパ|CHAR と VARCHAR (既定値)|  
    |cp850|DOS 西ヨーロッパ|CHAR と VARCHAR (既定値)|  
    |hp8|HP 西ヨーロッパ|CHAR と VARCHAR (既定値)|  
    |koi8r|KOI8 R Relcom ロシア語|CHAR と VARCHAR (既定値)|  
    |ラテン 1|cp1252 西ヨーロッパ|CHAR と VARCHAR (既定値)|  
    |latin2|ISO 8859-2 中央ヨーロッパ言語|CHAR と VARCHAR (既定値)|  
    |swe7|7 ビット スウェーデン語|CHAR と VARCHAR (既定値)|  
    |ascii|US ASCII|CHAR と VARCHAR (既定値)|  
    |ujis|EUC-JP 日本語|NCHAR と NVARCHAR (既定値)|  
    |sjis|Shift JIS の日本語|NCHAR と NVARCHAR (既定値)|  
    |ヘブライ語|ISO 8859-8 ヘブライ語|CHAR と VARCHAR (既定値)|  
    |tis620|TIS620 タイ語|CHAR と VARCHAR (既定値)|  
    |euckr|EUC-KR 韓国語|NCHAR と NVARCHAR (既定値)|  
    |koi8u|KOI8-u ウクライナ語|CHAR と VARCHAR (既定値)|  
    |gb2312|GB2312 簡体字中国語|NCHAR と NVARCHAR (既定値)|  
    |ギリシャ語|ISO 8859-7 ギリシャ語|CHAR と VARCHAR (既定値)|  
    |cp 1250|Windows の中央ヨーロッパ言語|CHAR と VARCHAR (既定値)|  
    |gbk|GBK 簡体字中国語|NCHAR と NVARCHAR (既定値)|  
    |ラテン 5|ISO 8859-3 トルコ語|CHAR と VARCHAR (既定値)|  
    |armscii8|ARMSCII 8 アルメニア語|CHAR と VARCHAR (既定値)|  
    |utf8|Utf-8 Unicode|NCHAR と NVARCHAR (既定値)|  
    |ucs2|Unicode の ucs-2|NCHAR と NVARCHAR (既定値)|  
    |いる cp866|DOS のロシア語|CHAR と VARCHAR (既定値)|  
    |keybcs2|DOS Kamenicky チェコ語-スロバキア語|CHAR と VARCHAR (既定値)|  
    |macce|Mac の中央ヨーロッパ言語|CHAR と VARCHAR (既定値)|  
    |macroman|Mac 西ヨーロッパ|CHAR と VARCHAR (既定値)|  
    |cp852|DOS 中央ヨーロッパ|CHAR と VARCHAR (既定値)|  
    |latin7|ISO 8859-13 バルト言語|CHAR と VARCHAR (既定値)|  
    |cp 1251|Windows (キリル)|CHAR と VARCHAR (既定値)|  
    |cp 1256|Windows アラビア語|CHAR と VARCHAR (既定値)|  
    |cp 1257|Windows バルト言語|CHAR と VARCHAR (既定値)|  
    |binary|バイナリの擬似文字セット|CHAR と VARCHAR (既定値)|  
    |geostd8|GEOSTD8 グルジア語|CHAR と VARCHAR (既定値)|  
    |cp932|Windows 日本語の SJIS|NCHAR と NVARCHAR (既定値)|  
    |eucjpms|Windows 日本語の UJIS|NCHAR と NVARCHAR (既定値)|  
  
2.  **データベース、カテゴリ、またはオブジェクト ノード レベルで:**データベース、カテゴリ、またはオブジェクトのノード レベルで、文字セットのマッピング グリッドに含まれるメタデータのルート ノード レベル、上の 1 つと同じ行 viz。  
  
    1.  タイトル、グリッドの最初の列**文字セット名**文字セットの名前が含まれています。  
  
    2.  という、2 番目の列**文字セットの説明**文字セットの説明が含まれています。  
  
    3.  唯一の違いは、グリッドの 3 番目の列の値です。 3 番目の列のタイトル、**対象のデータ型**特定の文字セットのマッピングの設定が含まれています。 列の値は次のとおりです。  
  
        -   継承 (CHAR と VARCHAR または NCHAR と NVARCHAR)  
  
        -   CHAR と VARCHAR  
  
        -   NCHAR/NVARCHAR  
  
> [!IMPORTANT]  
> -   MySQL データベースとデータベース、カテゴリ、およびオブジェクト ノード レベルでターゲット データベースの間の文字セット マッピングで、既定値列のルート以外のレベルごとに特定の文字セット**対象のデータ型**'を継承するか' です。  
> -   グリッドで、値**継承**いずれかのサフィックスが '(CHAR/VARCHAR)' または '(NCHAR/NVARCHAR)' によって、この特定の文字セットでは、どの値が親から継承がします。  
  
