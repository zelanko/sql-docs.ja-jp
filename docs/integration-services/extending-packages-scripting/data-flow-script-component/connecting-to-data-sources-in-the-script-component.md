---
title: "スクリプト コンポーネントでデータ ソースへの接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], connecting to data sources
ms.assetid: 96de63ab-ff48-4e7e-89e0-ffd6a89c63b6
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2accca553f1bd9c536076fd0bbcebbff0ff2c42
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-to-data-sources-in-the-script-component"></a>スクリプト コンポーネントでのデータ ソースへの接続
  接続マネージャーは、便宜上、特定の種類のデータ ソースに接続するために必要な情報をカプセル化して格納するユニットです。 詳細については、「[Integration Services &#40;SSIS&#41; の接続](../../../integration-services/connection-manager/integration-services-ssis-connections.md)」を参照してください。  
  
 利用できる既存の接続マネージャーのアクセス元または変換先コンポーネントでカスタム スクリプトによって をクリックして、**追加**と**削除**ボタン、**接続マネージャー**のページ、**スクリプト変換エディター**です。 ただし、データの読み込みや保存、場合によってはデータ ソースとの接続や切断を行うためには、独自のカスタム コードを記述する必要があります。 詳細については、**接続マネージャー**のページ、**スクリプト変換エディター**を参照してください[スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成する](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)と[スクリプト変換エディター & #40 です。接続マネージャー ページ &#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
 スクリプト コンポーネントを作成、**接続**コレクション クラスに、 **ComponentWrapper**をそれぞれの接続マネージャーを接続マネージャー自体と同じ名前を持つ、厳密に型指定されたアクセサーを含むプロジェクト項目です。 このコレクションは、によって公開される、**接続**のプロパティ、 **ScriptMain**クラスです。 アクセサー プロパティは、接続マネージャーへの参照を <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100> のインスタンスとして返します。 たとえば、ダイアログ ボックスの [接続マネージャー] ページで `MyADONETConnection` という名前の接続マネージャーを追加した場合、次のコードを追加することで、スクリプト内のその接続マネージャーへの参照を取得できます。  
  
 `Dim myADONETConnectionManager As IDTSConnectionManager100 = _`  
  
 `Me.Connections.MyADONETConnection`  
  
> [!NOTE]  
>  呼び出す前に、接続マネージャーによって返される接続の種類を知る必要があります**AcquireConnection**です。 スクリプト タスクではため**Option Strict**が有効な型として返されると、接続をキャストする必要があります**オブジェクト**、使用する前に適切な接続の種類にします。  
  
 次を呼び出す、 **AcquireConnection**基になる接続またはデータ ソースに接続するために必要な情報を取得する特定の接続マネージャーのメソッドです。 たとえばへの参照を取得、 **System.Data.SqlConnection**次のコードを使用して、ADO.NET 接続マネージャーによってラップします。  
  
 `Dim myADOConnection As SqlConnection = _`  
  
 `CType(MyADONETConnectionManager.AcquireConnection(Nothing), SqlConnection)`  
  
 これに対し、同じ呼び出しをフラット ファイル接続マネージャーに対して行った場合、ファイル データ ソースのパスとファイル名のみが返されます。  
  
 `Dim myFlatFile As String = _`  
  
 `CType(MyFlatFileConnectionManager.AcquireConnection(Nothing), String)`  
  
 このパスとファイル名を指定する必要がありますし、 **System.IO.StreamReader**または**Streamwriter**フラット ファイルのデータを読み書きします。  
  
> [!IMPORTANT]  
>  スクリプト コンポーネントでマネージ コードを記述すると、OLE DB 接続マネージャーや Excel 接続マネージャーなどのアンマネージ オブジェクトを返すマネージャー接続の AcquireConnection メソッドを呼び出すことはできません。 ただし、これらの接続マネージャーの ConnectionString プロパティを読み取るし、OLEDB の接続文字列を使用して、コード内で直接データ ソースへの接続**接続**から、 **System.Data.OleDb**名前空間。  
>   
>  アンマネージ オブジェクトを返す接続マネージャーの AcquireConnection メソッドを呼び出す必要がある場合は、ADO.NET 接続マネージャーを使用します。 OLE DB プロバイダーを使用するように ADO.NET 接続マネージャーを設定すると、接続には .NET Framework Data Provider for OLE DB が使用されます。 この場合、AcquireConnection メソッドを返します、 **system.data.oledb.oledbconnection で**アンマネージ オブジェクトの代わりにします。 Excel のデータ ソースを使用するための ADO.NET 接続マネージャーを構成するのに、Microsoft OLE DB Provider for Jet を選択、Excel ブックを指定し、入力`Excel 8.0`(Excel 97 以降) の値として**Extended Properties**上、**すべて**のページ、**接続マネージャー**  ダイアログ ボックス。  
  
 スクリプト コンポーネントによる接続マネージャーを使用する方法の詳細については、次を参照してください。[ソースを作成するスクリプト コンポーネントによる](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)と[スクリプト コンポーネントによる変換先の作成](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)です。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; の接続](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [接続マネージャーを作成します。](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  

