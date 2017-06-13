---
title: "カスタム アプリケーションで RSClientPrint コントロールを使用する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- RSPrintClient control
- print controls [Reporting Services]
- custom printing [Reporting Services]
- client-side printing
ms.assetid: 8c0bdd18-8905-4e22-9774-a240fc81a8a7
caps.latest.revision: 31
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8afee187160da9d35efd0c7079b649bac7e73740
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="using-the-rsclientprint-control-in-custom-applications"></a>カスタム アプリケーション内での RSClientPrint コントロールの使用
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ActiveX コントロール、 **RSPrintClient**、HTML ビューアーで表示されたレポートのクライアント側印刷機能します。 提供、**印刷** ダイアログ ボックスのユーザーしたりできるように、印刷ジョブを開始、レポートをプレビュー、印刷するページを指定の余白を変更します。 クライアント側での印刷操作の間、レポート サーバーが画像 (EMF) 表示拡張機能でレポートを表示し、オペレーティング システムの印刷機能を使用して印刷ジョブを作成し、そのジョブをプリンターに送ります。  
  
 クライアント側の印刷機能を使用すると、ユーザーのコンピューター上のブラウザーの印刷設定を使用せずに、レポートのページのサイズ、余白、ヘッダー テキスト、フッター テキストを使用して印刷出力を生成できるため、HTML レポートの印刷を制御して品質を向上させることができます。 このコントロールは、レポートのプロパティ値を読み込んで、ページ サイズと余白を設定します。  
  
 開発者向けのサードパーティのツールバーやビューアーでクライアント側印刷機能を有効にすることができますを使用して ActiveX コントロールへのアクセス、 **RSClientPrint** COM オブジェクトです。 このコントロールは自由に配布してかまいません。 以下にコントロールを使用するうえでの推奨事項を示します。  
  
-   コントロールを使用して、Web ベースのレポートの印刷を強化することができます。 いずれかで、オブジェクトを指定することができます、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-互換性のあるプログラミング言語またはスクリプトです。 このコントロールは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows フォーム アプリケーションからの利用は想定していません。  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] プログラム ファイルに含まれている .cab ファイルをコピーし、カスタム アプリケーションのコード ベースに追加します。  
  
-   使用して、\<オブジェクト > タグにコントロールを指定します。  
  
-   OBJECT CODEBASE 属性では、.cab ファイルに対する相対 URL または完全修飾 URL を指定します。  
  
-   アプリケーションで使用しているバージョンを追跡するため、.cab ファイルに対する固有のアプリケーション バージョン情報を指定します。  
  
-   オンライン ブックの画像 (EMF) 表示に関するトピックを参照し、印刷プレビューおよび出力用にページを表示する方法を確認します。  
  
## <a name="rsprintclient-overview"></a>RSPrintClient の概要  
 このコントロールによって表示されるカスタム印刷ダイアログ ボックスでは、印刷プレビュー、特定のページや範囲を指定するためのページ選択、ページ余白、ページの向きなど、一般的な印刷ダイアログ ボックスの機能がサポートされています。 コントロールは CAB ファイルとしてパッケージ化されています。 内のテキスト、**印刷** ダイアログ ボックスがすべてでサポートされる言語にローカライズされた[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 **RSPrintClient** ActiveX コントロールは、レポートを印刷する画像表示拡張機能 (EMF) を使用します。 EMF デバイス情報として StartPage、EndPage、MarginBottom、MarginLeft、MarginTop、MarginRight、PageHeight、および PageWidth が使用されます。 画像表示に対するその他のデバイス情報の設定はサポートされません。  
  
### <a name="language-support"></a>言語サポート  
 印刷コントロールでは、ユーザー インターフェイスのテキストがさまざまな言語で表示され、異なる測定系を使用した入力値を受け付けます。 によって使用される言語と測定系が決定されます、**カルチャ**と**UICulture**プロパティです。 どちらのプロパティも LCID 値を受け付けます。 サポートされている言語から派生した言語の LCID を指定すると、最も近い言語が選択されます。 サポート対象外で、近い言語もない LCID を指定すると、英語 (U.S.) となります。  
  
## <a name="using-rsclientprint-in-code"></a>コード内での RSClientPrint の使用  
 **RSClientPrint**オブジェクトは、ActiveX コントロールとそのメソッドおよびプロパティをプログラムでアクセスするために使用します。 このコントロールでは、印刷プレビュー用のモーダル ダイアログが提供されます。  
  
### <a name="specifying-default-values"></a>既定値の指定  
 初期化するには、**印刷** ダイアログ ボックス、レポートの余白やページの値。 既定では、**印刷** ダイアログ ボックスはレポート定義の値で初期化します。 既定値を使用することも、オブジェクトのプロパティを設定して異なる値を指定することもできます。  
  
 サイズはすべて mm 単位で設定されます。 場合、実行時に単位が変換が発生した、**カルチャ**と**UICulture**メートル法を使わないロケールに設定されます。  
  
 使用される値をページのサイズと余白の詳細については、使用することができます、 **GetProperties**を既定値を取得する方法。  
  
-   **PageHeight**と**PageWidth**既定のページの高さと幅を指定します。 印刷コントロールを起動すると、現在選択されているプリンターで利用できる用紙サイズの中から、これらのプロパティ値に最も近いサイズが選択されます。 場合**PageWidth**がより優れた**PageHeight**、印刷の向きは横 に設定します。 そうでない場合は縦向きに設定されます。  
  
-   **LeftMargin**、 **RightMargin**、 **TopMargin**、および**BottomMargin**はすべて 12.2 ミリメートル既定に設定します。  
  
 これらのプロパティに格納されている、**項目**レポート サーバーのプロパティのコレクション。 値は、レポート定義が更新されるたびに上書きされます。  
  
### <a name="rsclientprint-properties"></a>RSClientPrint プロパティ  
  
|プロパティ|型|RW|既定値|Description|  
|--------------|----------|--------|-------------|-----------------|  
|MarginLeft|Double|RW|レポートにより設定|左余白を取得または設定します。 開発者が設定せず、レポートにも指定がない場合の既定値は 12.2 mm です。|  
|MarginRight|Double|RW|レポートにより設定|右余白を取得または設定します。 開発者が設定せず、レポートにも指定がない場合の既定値は 12.2 mm です。|  
|MarginTop|Double|RW|レポートにより設定|上余白を取得または設定します。 開発者が設定せず、レポートにも指定がない場合の既定値は 12.2 mm です。|  
|MarginBottom|Double|RW|レポートにより設定|下余白を取得または設定します。 開発者が設定せず、レポートにも指定がない場合の既定値は 12.2 mm です。|  
|PageWidth|Double|RW|レポートにより設定|ページの幅を取得または設定します。 開発者が設定せず、レポートにも定義がない場合の既定値は 215.9 mm です。|  
|PageHeight|Double|RW|レポートにより設定|ページの高さを取得または設定します。 開発者が設定せず、レポートにも定義がない場合の既定値は 279.4 mm です。|  
|カルチャ|Int32|RW|ブラウザーのロケール|ロケール ID (LCID) を指定します。 この値によりユーザー入力の測定単位が決まります。 たとえば、ユーザーが**3**言語がフランス語またはインチの言語が英語 (米国) である場合にその値がミリメートル単位で測定されます。 有効な値は、1028、1031、1033、1036、1040、1041、1042、2052、3082 です。|  
|UICulture|文字列|RW|クライアントのカルチャ|ダイアログ ボックスの文字列のローカライズを指定します。 [印刷] ダイアログ内のテキストは、簡体字中国語、繁体字中国語、英語、フランス語、ドイツ語、イタリア語、日本語、韓国語、スペイン語にローカライズされています。 有効な値は、1028、1031、1033、1036、1040、1041、1042、2052、3082 です。|  
|Authenticate|ブール値|RW|False|セッション外印刷の接続を開始するためにコントロールからレポート サーバーに GET コマンドを発行するかどうかを指定します。|  
  
### <a name="when-to-set-the-authenticate-property"></a>Authenticate プロパティを設定する状況  
 ブラウザー セッションの内部から印刷する場合は設定する必要はありません、**認証**プロパティです。 アクティブなセッションのコンテキストでは、印刷コントロールからレポート サーバーへの要求はすべてブラウザーによって処理されます。 レポート サーバーへの通信に必要なセッション変数はブラウザーによって設定されます。  
  
 印刷コントロールが HTTP を発行する必要があります (たとえば、最初に開かずをプリンターに直接レポートを送信) - セッションの出力を印刷する場合**取得**要求をレポート サーバーでセッションを設定します。 発行する、**取得**要求を設定する**認証**に**True**です。  
  
 だけを発行する必要があります、**取得**セキュリティまたは基本認証に Windows を使用している場合、要求が統合されています。 フォーム認証を使用している場合、**認証**プロパティは無視されます。 アプリケーション コードでセッションを設定し、用意したカスタム セキュリティ拡張機能を使用してユーザーを認証する必要があります。 フォーム認証を使用する場合は、認証クッキーの有効期限を、セッションが十分な期間にわたって維持される値に設定してください。 この値を低く設定しすぎると、クッキーの有効期限が切れるたびに、ユーザーにログオン資格情報の入力が要求されます。  
  
### <a name="clsids"></a>Clsid  
 レポートをオンプレミスで実行している場合は、次の CLSID 値を使用します。  
  
-   41861299-EAB2-4DCC-986C-802AE12AC499  
  
-   5554DCB0-700B-498D-9B58-4E40E5814405  
  
-   60677965-AB8B-464f-9B04-4BA871A2F17F  
  
 レポートを Windows Azure SQL Reporting で実行している場合は、次の CLSID 値を使用します。  
  
-   3DD32426-554D-48C0-A200-65D3BF880E38  
  
-   05662494-ACF9-446A-BE4C-7D3F7EA7F62F  
  
### <a name="rsprintclient-support-for-the-print-method"></a>RSPrintClient による Print メソッドのサポート  
 **RSClientPrint**オブジェクトのサポート、**印刷**メソッドは、[印刷] ダイアログ ボックスを起動するために使用します。 **印刷**メソッドには、次の引数。  
  
|引数|I/O|型|Description|  
|--------------|----------|----------|-----------------|  
|ServerPath|In|文字列|レポート サーバーの仮想ディレクトリを指定します (たとえば、 `https://adventure-works/reportserver`)。|  
|ReportPathParameters|In|文字列|パラメーターを含む、レポート サーバー フォルダー名前空間内のレポートの完全な名前を指定します。 レポートは、URL にアクセスすることによって取得されます。 たとえば、「/AdventureWorks Sample Reports/Employee Sales Summary&EmpID=1234」のように指定します。|  
|ReportName|In|文字列|レポートの短縮名です (上の例では、短縮名は「Employee Sales Summary」です)。 ここで設定した内容は、[印刷] ダイアログ ボックスと印刷キューに表示されます。|  
  
### <a name="example"></a>例  
 次の HTML の例は、.cab ファイルを指定する方法を示しています。**印刷**メソッド、および JavaScript でのプロパティ。  
  
 `<BODY onload="Print()">`  
  
 `<OBJECT ID="RSClientPrint" CLASSID="CLSID: 5554DCB0-700B-498D-9B58-4E40E5814405D3" CODEBASE="<URL to the .CAB file>#Version=<your application version information>" VIEWASTEXT></OBJECT>`  
  
 `<script language="javascript">`  
  
 `function Print()`  
  
 `{`  
  
 `RSClientPrint.MarginLeft = 12.7;`  
  
 `RSClientPrint.MarginTop = 12.7;`  
  
 `RSClientPrint.MarginRight = 12.7;`  
  
 `RSClientPrint.MarginBottom = 12.7;`  
  
 `RSClientPrint.Culture = 1033;`  
  
 `RSClientPrint.UICulture = 9;`  
  
 `RSClientPrint.Print('http://localhost/rtm', '%2fEmployee_Sales_Summary&ReportMonth=6&ReportYear=2004&EmpID=20', 'Employee_Sales_Summary')`  
  
 `}`  
  
 `</script>`  
  
 `</BODY>`  
  
## <a name="see-also"></a>参照  
 [印刷の管理 &#40; を使用したブラウザーからレポートの印刷レポート ビルダーおよび SSRS &#41;](../../../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)   
 [レポートの印刷 & #40 です。レポート ビルダーおよび SSRS &#41;](../../../reporting-services/report-builder/print-reports-report-builder-and-ssrs.md)   
 [画像デバイス情報設定](../../../reporting-services/image-device-information-settings.md)  
  
  
