---
title: "ConnectionString プロパティ (ADO) |Microsoft ドキュメント"
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
- Connection15::ConnectionString
helpviewer_keywords:
- ConnectionString property [ADO]
ms.assetid: 3be75b75-4d36-4479-ab64-9a456869252a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aaf33c9a4fd5b628307195b9b9a7d1743d24d7f2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="connectionstring-property-ado"></a>ConnectionString プロパティ (ADO)
データ ソースへの接続を確立するために使用される情報を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**値。  
  
## <a name="remarks"></a>解説  
 使用して、 **ConnectionString**プロパティを含む、一連の詳細な接続文字列を渡すことによって、データ ソースを指定する*引数**値 =*で区切られたステートメントセミコロン入力します。  
  
 ADO の 5 つの引数をサポートする、 **ConnectionString**プロパティ; ADO で処理されず、プロバイダーに直接その他の引数のパス。 引数の ADO サポートは次のとおりです。  
  
|引数|Description|  
|--------------|-----------------|  
|*Provider=*|接続に使用するプロバイダーの名前を指定します。|  
|*ファイル名 =*|事前設定された接続情報を含むプロバイダー固有のファイル (たとえば、永続化されたデータ ソース オブジェクト) の名前を指定します。|  
|*リモート プロバイダー =*|クライアント側の接続を開くときに使用するプロバイダーの名前を指定します。 (リモート データのサービスのみ。)|  
|*リモート サーバー =*|クライアント側の接続を開くときに使用するサーバーのパス名を指定します。 (リモート データのサービスのみ。)|  
|*URL=*|ファイルまたはディレクトリなどのリソースを識別する絶対 URL として接続文字列を指定します。|  
  
 設定した後、 **ConnectionString**プロパティと open、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト、プロバイダー可能性がありますの内容が変更プロパティは、たとえば、ADO 定義の引数名をマップすることによって、特定のプロバイダーに対応します。  
  
 **ConnectionString**プロパティで使用される値を自動的に継承する、 *ConnectionString*の引数、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)現在をオーバーライドするためのメソッド**ConnectionString**中にプロパティ、**開く**メソッドの呼び出しです。  
  
 *ファイル名*引数すると、ADO では、関連付けられているプロバイダーを読み込み、両方を渡すことはできません、*プロバイダー*と*ファイル名*引数。  
  
 **ConnectionString**プロパティが読み取り/書き込みが開いているとき、接続が閉じていて、読み取り専用です。  
  
 内の引数の重複、 **ConnectionString**プロパティは無視されます。 いずれかの引数の最後のインスタンスが使用されます。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側で使用すると**接続**オブジェクト、 **ConnectionString**プロパティにのみを含めることができます、*リモート プロバイダー*と*リモート サーバー*パラメーター。  
  
 次の表に、各 Windows オペレーティング システムの既定の ADO プロバイダーを示します。  
  
|既定の ADO プロバイダー|Windows オペレーティング システム|  
|--------------------------|------------------------------|  
|MSDASQL<br /><br /> (ソース コードの読みやすさを向上させるのに明示的に指定プロバイダーの名前、接続文字列に)。|Windows 2000 (32 ビット)<br /><br /> Windows XP (32 ビット)<br /><br /> Windows Server 2003 (32 ビット)<br /><br /> Windows Vista (32 ビット)<br /><br /> Windows Vista Service Pack 1 またはそれ以降 (32 ビットおよび 64 ビット)<br /><br /> Windows Vista (32 ビットおよび 64 ビット) の後のバージョンの Windows|  
|既定値はありません。<br /><br /> ADO アプリケーションでは、次のオペレーティング システムで実行され、プロバイダーが明示的に指定しない、ときに、次のエラーが返されます。"ADODB です。接続: プロバイダーが指定されていないと、指定された既定のプロバイダーがありません"|Windows 2000 (64 ビット)<br /><br /> Windows XP (64 ビット)<br /><br /> Windows Server 2003 (64 ビット)<br /><br /> Windows Vista (64 ビット)|  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ConnectionString、ConnectionTimeout、および (VB) の状態プロパティの例](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、ConnectionTimeout、および (vc++) の状態プロパティの例](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
