---
title: "DataControl オブジェクト (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- DataControl
- RDS.DataControl
helpviewer_keywords:
- DataControl object [ADO]
ms.assetid: d85ea4fc-451c-436e-97b8-58f92b149dd0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d7b3e0927f902f52138cdb37091df14652845fa4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="datacontrol-object-rds"></a>DataControl オブジェクト (RDS)
データ クエリ バインド[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)1 つまたは複数のコントロール (たとえば、テキスト ボックス、取引先グリッド コントロールまたはコンボ ボックス) を表示する、 **Recordset** Web ページ上のデータ。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="http://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
</OBJECT>  
```  
  
## <a name="remarks"></a>解説  
 クラス ID、 **.rds ですDataControl**オブジェクトが BD96C556 65A3-11-d 0 983A 00C04FC29E33 です。  
  
> [!NOTE]
>  エラーを取得する場合、 [.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)または**.rds ですDataControl**オブジェクトにありませんロードは、正しいクラス ID を使用していることを確認してください クラスのこれらのオブジェクト Id は、バージョン 1.0 および 1.1 から変更されました。 また、注意を使用するときにも null 許容の列を設定する必要がある、 **RDS DataControl**オブジェクト。  
  
 基本的なシナリオでは、のみを設定する必要があります、 **SQL**、**接続**、および**サーバー**のプロパティ、 **.rds ですDataControl**オブジェクトで、既定のビジネス オブジェクトの呼び出しに自動的には、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)です。  
  
 内のすべてのプロパティ、 **.rds ですDataControl**は省略可能なカスタム ビジネス オブジェクトがそれらの機能を置き換えることができます。  
  
> [!NOTE]
>  複数の結果を得るには、照会する場合は、最初のメッセージだけ[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)が返されます。 複数の結果セットが必要な場合は、それぞれ独自に割り当てる**DataControl**です。 複数の結果のクエリの例は、以下である可能性があります。`"Select * from Authors, Select * from Topics"`  
  
 追加する"DFMode = 20 です"を使用すると接続文字列、 **.rds です。DataControl**データを更新するときに、オブジェクトが、サーバーのパフォーマンスを向上させることができます。 この設定で、 **RDSServer.DataFactory**サーバー上のオブジェクトで少ないリソースを消費するモードを使用します。 ただし、次の機能では、この構成では利用できません。  
  
-   パラメーター化クエリを使用します。  
  
-   パラメーターまたは列の情報を呼び出す前に取得、 **Execute**メソッドです。  
  
-   設定**更新プログラムを Transact**に**True**です。  
  
-   行の状態を取得します。  
  
-   呼び出す、[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドです。  
  
-   使用して (明示的にまたは自動的に) を更新する、[更新プログラムが再同期](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)プロパティです。  
  
-   設定**コマンド**または[Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md)プロパティです。  
  
-   使用して**adCmdTableDirect**です。  
  
 **.Rds ですDataControl**オブジェクトは既定で非同期モードで実行します。 アプリケーションの同期実行する場合、設定、 [ExecuteOptions](../../../ado/reference/rds-api/executeoptions-property-rds.md)パラメーターと等しい**adcExecSync**と[FetchOptions](../../../ado/reference/rds-api/fetchoptions-property-rds.md) に等しいパラメーター**adcFetchUpFront**の次の例に示すようにします。  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"   
    ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="http://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
   <PARAM NAME="ExecuteOptions" VALUE="1">   <PARAM NAME="FetchOptions" VALUE="1">  
</OBJECT>  
```  
  
 1 つを使用して**.rds ですDataControl** 1 つまたは複数のビジュアル コントロールに 1 つのクエリの結果をリンクするオブジェクト。 たとえば、名前、住所、出生、年齢、および優先順位の顧客のステータスなどのクエリ要求している顧客データをコードがあるとします。 1 つを使用する**.rds ですDataControl** ; 次の 3 つの別々 のテキスト ボックスに、顧客の名前、年齢、および領域を表示するオブジェクト優先順位の顧客のステータス チェック ボックスです。グリッド コントロール内のすべてのデータ。  
  
 使用して異なる**.rds ですDataControl** visual にさまざまなコントロールに複数のクエリの結果をリンクするオブジェクト。 たとえば、1 つのクエリを顧客に関する情報を取得して、顧客が購入した商品に関する情報を取得する 2 番目のクエリを使用するとします。 3 つのテキスト ボックスと 1 つのチェック ボックス、グリッド コントロールで 2 番目のクエリの結果の最初のクエリの結果を表示するには。 既定のビジネス オブジェクトを使用する場合 (**RDSServer.DataFactory**)、次を行う必要があります。  
  
-   2 つ追加**.rds ですDataControl** Web ページにオブジェクト。  
  
-   2 つの書き込みがクエリごとに 1 つ**SQL** 、2 つのプロパティ**.rds ですDataControl**オブジェクト。 1 つ**.rds ですDataControl**オブジェクトが顧客情報を要求する SQL クエリに含まれますが、2 番目には、顧客が購入した商品の一覧を要求するクエリが格納されています。  
  
-   各バインドされたコントロールの OBJECT タグでは、各ビジュアル コントロールに表示するデータの値を設定する DATAFLD 値を指定します。  
  
 数のカウントの制限はありません**.rds ですDataControl**オブジェクトを 1 つの Web ページに OBJECT タグを使用して、埋め込むことができます。  
  
 定義するときに、 **.rds ですDataControl** Web ページ上のオブジェクト、0 以外を使用して**高さ**と**幅**を避けるために余分なスペースを含めること) 1 などの値。  
  
 リモートのデータ サービス クライアント コンポーネントが Internet Explorer 4.0; の一部として含まれています。そのため、必要はありませんでコードベースのパラメーターを含む、 **.rds ですDataControl** object タグ。  
  
 Internet Explorer 4.0 以降、アパートメント モデルのコントロールとしてマークされている場合にのみ、HTML コントロールおよび ActiveX® コントロールを使用してデータにバインドできます。  
  
> [!NOTE]
>  **Microsoft Visual Basic ユーザー** 、 **.rds ですDataControl**がスクリプトに対して安全とは Web ベースのアプリケーションでのみ使用します。 Visual Basic クライアント アプリケーションでは、その必要はありません。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [DataControl オブジェクト (RDS) のプロパティ、メソッド、およびイベント](../../../ado/reference/rds-api/datacontrol-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [DataControl オブジェクトの例 (VBScript)](../../../ado/reference/rds-api/datacontrol-object-example-vbscript.md)






















