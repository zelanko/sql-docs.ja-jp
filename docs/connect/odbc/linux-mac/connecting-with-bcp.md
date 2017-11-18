---
title: "Bcp を使用した接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bcp
ms.assetid: 3eca5717-e50f-40db-be16-a1cebbdfee70
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1d2c7f5346d3d834a14161da188733cd72dcede1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-with-bcp"></a>bcp による接続
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

[Bcp](http://go.microsoft.com/fwlink/?LinkID=190626)ユーティリティでは、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux や macOS にします。 このページの Windows のバージョンとの相違点について説明`bcp`です。
  
- フィールド ターミネータはタブ ("\t") です。  
  
- 行ターミネータは改行 ("\n") です。  
  
- キャラクター モードで推奨される形式の`bcp`ファイルと拡張文字を含まないデータ ファイルの書式を設定します。  
  
> [!NOTE]  
> 円記号 '\\' に、コマンドライン引数を引用符で囲まれたか、エスケープするか、必要があります。 たとえば、カスタム行ターミネータとして改行文字を指定するにする必要がありますを使用して、次のメカニズムのいずれかの。  
>   
> -   -r\\\n  
> -   -r"\n"  
> -   -r'\n'  
  
呼び出しの例のコマンドを次に示します`bcp`テーブルの行をテキスト ファイルにコピーします。  
  
```  
bcp AdventureWorks2008R2.Person.Address out test.dat -Usa -Pxxxx -Sxxx.xxx.xxx.xxx  
```  
  
## <a name="available-options"></a>使用可能なオプション
現在のリリースでは、次の構文とオプションを使用できます。  

[*database***.**]*schema***.***table* **in** *data_file* | **out** *data_file*

- -a *packet_size*  
サーバーとの間で送信されるネットワーク パケットごとのバイト数を指定します。  
  
- -b *batch_size*  
一括インポートするデータの行数を指定します。  
  
- -c  
文字データ型を使用します。  
  
- -d *database_name*  
接続先のデータベースを指定します。  
  
- -d  
渡された値により、`bcp`データ ソース名 (DSN) として解釈するで、-s オプション。 詳細については、「sqlcmd および bcp の DSN サポート」を参照してください[sqlcmd による接続](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)です。  
  
- -e *error_file*行を格納するエラー ファイルの完全パスを指定します、`bcp`ユーティリティによって、あるファイルからデータベースに転送することはできません。  
  
- -e  
ID 列に、インポートされたデータ ファイルの ID 値を使用します。  
  
- -f *format_file*  
フォーマット ファイルの完全パスを指定します。  
  
- -F *first_row*  
テーブルからエクスポートする最初の行、またはデータ ファイルからインポートする最初の行の番号を指定します。  
  
- -k  
一括コピー操作時、空の列には、挿入される列の既定値ではなく、NULL 値が保持されます。  
  
- -l  
ログインのタイムアウトを指定します。 – L オプションにログインするまでの秒数を指定する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]がタイムアウトになるサーバーに接続しようとします。 既定のログイン タイムアウトは、15 秒です。 ログイン タイムアウトは、0 ~ 65,534 の範囲の数値でなければなりません。 指定した値が数値以外の場合、または範囲外の場合、`bcp` はエラー メッセージを生成します。 値 0 は、無限のタイムアウトを指定します。
  
- -L *last_row*  
テーブルからエクスポートする最後の行、またはデータ ファイルからインポートする最後の行の番号を指定します。  
  
- -m *max_errors*  
前に発生する可能性がある構文エラーの最大数を指定、`bcp`操作が取り消されました。  
  
- -n  
データのネイティブの (データベース) データ型を使用して一括コピー操作を実行します。  
  
- -P *password*  
ログイン ID のパスワードを指定します。  
  
- -Q  
`bcp` ユーティリティと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] のインスタンスとの接続で、SET QUOTED_IDENTIFIERS ON ステートメントを実行します。  
  
- -r *row_terminator*  
行ターミネータを指定します。  
  
- -r  
通貨、日付、時刻のデータを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] に一括コピーする場合に、クライアント コンピューターのロケール設定に定義された地域別設定が使用されます。  
  
- -S *server*  
名前を指定、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]接続先のインスタンスまたは-d が使用される、DSN。  
  
- -t *field_terminator*  
フィールド ターミネータを指定します。  
  
- -T  
指定する、`bcp`ユーティリティに接続[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]信頼された接続 (統合セキュリティ) を使用します。  
  
- -U *login_id*  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] への接続に使用されるログイン ID を指定します。  
  
- -v  
`bcp` ユーティリティ バージョン番号と著作権に関する情報を報告します。  
  
- -w  
Unicode 文字を使用して一括コピー操作を実行します。  
  
このリリースでは、Latin-1 および UTF-16 文字がサポートされています。  
  
## <a name="unavailable-options"></a>利用できないオプション
現在のリリースでは、次の構文とオプションは利用できません。  

- -c  
データ ファイル内のデータのコード ページを指定します。  
  
- -h *hint*  
データをテーブルまたはビューに一括インポートするときに使用するヒントを指定します。  
  
- -i *input_file*  
応答ファイルの名前を指定します。  
  
- -n  
文字ではないデータにはネイティブな (データベース) データ型を使用し、文字データには Unicode 文字を使用します。  
  
- -o *output_file*  
コマンド プロンプトからリダイレクトされた出力を受け取るファイル名を指定します。  
  
- -V (80 | 90 | 100)  
以前のバージョンからのデータ型を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
- -x  
フォーマットおよび -f format_file オプションと共に使用し、既定の XML ではないフォーマット ファイルの代わりに XML ベースのフォーマット ファイルを生成します。  
  
## <a name="see-also"></a>参照

[使用した接続**sqlcmd**](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)  

