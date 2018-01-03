---
title: "選択して、テスト (SybaseToSQL) にオブジェクトの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Parameter Comparision Setting
- Tester Component,Selecting Objects
ms.assetid: 89c23aad-bfee-4917-bc16-175288390ac0
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 23c5a636c3031fce08294de4640799fde34362d7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-and-configuring-objects-to-test-sybasetosql"></a>選択して、テスト (SybaseToSQL) にオブジェクトの構成
この手順では、テスト、およびプロシージャの関数の出力パラメーターと関数の戻り値を比較するための設定を構成するオブジェクトを選択します。  
  
## <a name="selection-of-objects-to-test"></a>テストするオブジェクトの選択  
Sybase オブジェクト ツリーで、ウィンドウの左側にある、テスト プロセス中に、呼び出し先のオブジェクトを確認してください。 内のテストが容易なオブジェクトの完全な一覧を参照してください、[移行対象のデータベース オブジェクトのテストと #40 です。SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)トピックです。  
  
SSMA テスターによってサポートされないテスト用に選択されたオブジェクトのいずれかの場合は、ラベルの付いたリンクが表示されます**によって選択したオブジェクトには、エラーが含まれている**[オブジェクト] ツリー。 なぜこれらのオブジェクトをテストすることはできません、上の理由からや不適切なオブジェクトの選択を解除するは、このリンクをクリックします。  
  
右側にあるいくつかのページを表示することができます、 **SQL**ページは、現在のオブジェクトの定義を示しています。 **前 SQL**と**Post SQL**ページがテスト オブジェクトを開始の呼び出しの前後に実行するスクリプトを指定できます。 これは、オブジェクトは、このような一時テーブルまたはカーソルに他のオブジェクトを必要とする場合に役立ちます可能性があります。 **パラメーター**ページは、オブジェクトがストアド プロシージャまたは関数の場合、パラメーターを一覧表示されます。 **プロパティ**ページは、オブジェクトの他の特性を示しています。 説明を参照して**パラメーター Comparsions**と**呼び出す値**以下のページです。  
  
## <a name="parameter-comparison-settings"></a>パラメーターの比較の設定  
出力パラメーターの比較規則を確立し、内の値を返す、**パラメーターを比較する**ページ。 次の設定を行うことができます。  
  
### <a name="use-during-comparisons"></a>比較の際に使用します。  
テスト結果の比較では、選択したパラメーターの使用を有効にします。  
  
-   選択した場合**True**SSMA はで対応する値を持つ Sybase でプロシージャを実行した後はこのパラメーターの出力値を比較[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
-   選択した場合**False**パラメーター、結果の検証から除外されます。  
  
### <a name="use-custom-scale"></a>カスタムのスケールを使用します。  
概数と固定長の数値データ型パラメーターの場合、比較のためのカスタムのスケールを設定できます。  
  
-   選択した場合**True**によると、数値は丸められます、**を比較するスケール**値の比較がします。  
  
-   選択した場合**False**、数値比較を正確になります。  
  
### <a name="comparing-scale"></a>スケールの比較  
使用可能な場合にのみ、**使用縮尺**オプションに設定されて**True**です。 これは、数値比較の有効桁数です。  
  
### <a name="date-time-comparing"></a>日付時刻を比較します。  
定義方法、日付/時刻値が比較されます。  
  
-   選択した場合**全体の日付を比較**、両方のプラットフォームからの値の詳しい比較が行われます。  
  
-   選択した場合**日付のみを比較**、時刻部分は無視されます。  
  
-   選択した場合**時刻のみを比較**日付の部分は無視されます。  
  
-   選択した場合**(ミリ秒) を無視する**結果は、秒までと比較されます。  
  
-   選択した場合**無視日時 (ミリ秒)**、1 秒あたりの時間部分でのみ比較し、無視の小数部になります。  
  
### <a name="ignore-strings-case"></a>文字列の大文字小文字を区別します。  
比較の大文字小文字の区別を制御します。  
  
-   選択した場合**True**比較は大文字小文字を区別されます。  
  
-   選択した場合**False**比較は大文字と小文字が区別されます。  
  
### <a name="ignore-trailing-spaces"></a>[末尾のスペースを無視する]  
どの末尾のスペースを制御比較時に扱われます。  
  
-   選択した場合**True**、比較対象の文字列になります右トリム比較する前にします。  
  
-   選択した場合**False**、比較対象の文字列の末尾の空白は保持されます。  
  
## <a name="specify-input-values-for-procedures-and-functions-call-values"></a>プロシージャおよび関数 (呼び出し値) の入力値を指定します  
入力パラメーター値を指定することができます、**呼び出す値**ページ。 **の呼び出しの追加**ボタンは、空のパラメーター値を持つ新しい呼び出しを追加します。 **呼び出す削除**ボタンは、現在の呼び出しを削除します。  
  
## <a name="next-step"></a>次の手順  
[選択して、影響を受けるオブジェクト &#40; を構成します。SybaseToSQL &#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
  
## <a name="see-also"></a>参照  
[データベース オブジェクト &#40; 移行テストSybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
