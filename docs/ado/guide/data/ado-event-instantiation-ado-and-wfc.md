---
title: 'ADO イベントのインスタンス化: ADO と WFC |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9ee4be21-657b-407a-afa4-0b27a6b096ce
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1a4bb76e9172458c26e59dc366e8a321a548f34e
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702607"
---
# <a name="ado-event-instantiation-ado-and-wfc"></a>ADO イベントのインスタンス化: ADO と WFC
ADO の Windows Foundation Class (ADO と WFC) では、ADO イベント モデルの構築し、簡略化されたアプリケーション プログラミング インターフェイスを示します。 一般に、ADO と WFC ADO イベントを取得、1 つのイベント クラスにイベント パラメーターを統合し、イベント ハンドラーを呼び出します。  
  
### <a name="to-use-ado-events-in-adowfc"></a>ADO と WFC で ADO イベントを使用するには  
  
1.  イベントを処理する独自のイベント ハンドラーを定義します。 たとえば、処理する場合は、 **ConnectComplete**内のイベント、 **ConnectionEvent**ファミリ、する可能性がありますを使用して、このコード。  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    {  
        System.out.println("onConnectComplete:" + e);  
    }  
    ```  
  
2.  ハンドラーをイベント ハンドラーを表すオブジェクトを定義します。 ハンドラー オブジェクトは、データ型でなければなりません**ConnectEventHandler**型のイベントの**ConnectionEvent**、またはデータ型**RecordsetEventHandler** の種類のイベント**RecordsetEvent**します。 たとえばは、次のコード、 **ConnectComplete**イベント ハンドラー。  
  
    ```  
    ConnectionEventHandler handler =   
        new ConnectionEventHandler(this, "onConnectComplete");  
    ```  
  
     最初の引数、 **ConnectionEventHandler**コンス トラクターは、2 番目の引数で指定されたイベント ハンドラーを含むクラスへの参照。  
  
3.  特定の種類のイベントを処理するためのハンドラーの一覧に、イベント ハンドラーを追加します。 など、名前のメソッドを使用して **addOn** * EventName*(*ハンドラー*)。  
  
4.  ADO と WFC は内部的には、すべての ADO イベント ハンドラーを実装します。 そのため、イベントに起因、**接続**または**レコード セット**操作は、ADO と WFC イベント ハンドラーによって傍受します。  
  
     ADO と WFC イベント ハンドラーに渡します ADO **ConnectionEvent** ADO と WFC のインスタンス内のパラメーター **ConnectionEvent**クラス、または ADO **RecordsetEvent**パラメーターで、ADO と WFC のインスタンス**RecordsetEvent**クラス。 これらの ADO と WFC クラスは ADO イベントのパラメーターを統合します。つまり、各 ADO と WFC クラスにはすべての ADO の一意な各パラメーターの 1 つのデータ メンバーが含まれます**ConnectionEvent**または**RecordsetEvent**メソッド。  
  
5.  ADO と WFC は、ADO と WFC イベント オブジェクトにイベント ハンドラーを呼び出します。 たとえば、 **onConnectComplete**ハンドラーがこのような署名。  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    ```  
  
     最初の引数は、イベントを送信したオブジェクトの種類 ([接続](../../../ado/reference/ado-api/connection-object-ado.md)または[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md))、2 番目の引数は、ADO と WFC イベント オブジェクト (**ConnectionEvent**または**RecordsetEvent**)。  
  
     イベント ハンドラーのシグネチャは、ADO イベントよりも簡単です。 ただし、イベントに適用するパラメーターと対応する方法を知っている ADO イベント モデルを理解する必要があります。  
  
6.  ADO イベントの ADO と WFC ハンドラーにイベント ハンドラーから戻ります。 ADO と WFC ADO イベントのパラメーターに適切な ADO と WFC イベント データ メンバーをコピーし、ADO のイベント ハンドラーを返します。  
  
7.  完了したら、ADO と WFC イベント ハンドラーの一覧から、ハンドラーの削除を処理する。 など、名前のメソッドを使用して **removeOn** * EventName*(*ハンドラー*)。  
  
## <a name="see-also"></a>参照  
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO - WFC 構文のインデックス](../../../ado/reference/ado-api/ado-wfc-syntax-index.md)   
 [イベント パラメーター](../../../ado/guide/data/event-parameters.md)   
 [イベント ハンドラーの連携](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [イベントの種類](../../../ado/guide/data/types-of-events.md)
