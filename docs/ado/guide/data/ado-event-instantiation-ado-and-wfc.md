---
title: 'ADO イベントのインスタンス化: ADO および WFC |Microsoft ドキュメント'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9ee4be21-657b-407a-afa4-0b27a6b096ce
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6aa227f5ca6b6246d61e183c03d6217ebaa70bac
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270811"
---
# <a name="ado-event-instantiation-ado-and-wfc"></a>ADO イベントのインスタンス化: ADO および WFC
ADO の Windows Foundation Class (ADO/WFC) は、ADO イベント モデルでビルドし、簡略化されたアプリケーション プログラミング インターフェイスを提供します。 一般に、ADO/WFC ADO イベントを取得、イベント パラメーターに 1 つのイベント クラスでは、統合し、イベント ハンドラーを呼び出します。  
  
### <a name="to-use-ado-events-in-adowfc"></a>ADO/WFC で ADO イベントを使用するには  
  
1.  イベントを処理するイベント ハンドラーを定義します。 たとえば、処理する場合は、 **ConnectComplete**内のイベント、 **ConnectionEvent**ファミリを使用するこのコード。  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    {  
        System.out.println("onConnectComplete:" + e);  
    }  
    ```  
  
2.  イベント ハンドラーを表すハンドラー オブジェクトを定義します。 ハンドラー オブジェクトは、データ型でなければなりません**ConnectEventHandler**型のイベントの**ConnectionEvent**、またはデータ型**RecordsetEventHandler** の種類のイベント**RecordsetEvent**です。 たとえばは、次のコード、 **ConnectComplete**イベントのハンドラー。  
  
    ```  
    ConnectionEventHandler handler =   
        new ConnectionEventHandler(this, "onConnectComplete");  
    ```  
  
     最初の引数、 **ConnectionEventHandler**コンス トラクターは、2 番目の引数で指定されたイベント ハンドラーを含むクラスへの参照。  
  
3.  特定の種類のイベントを処理するためのハンドラーの一覧を表示、イベント ハンドラーを追加します。 など、名前のメソッドを使用して **addOn** * EventName*(*ハンドラー*)。  
  
4.  ADO/WFC は内部的には、ADO のすべてのイベント ハンドラーを実装します。 によってこのため、イベントの原因となった、**接続**または**レコード セット**ADO/WFC イベント ハンドラーによって操作が傍受します。  
  
     ADO/WFC イベント ハンドラーは、ADO を渡します**ConnectionEvent** ADO/WFC のインスタンス内のパラメーター **ConnectionEvent**クラス、または ADO **RecordsetEvent**パラメーターで、ADO/WFC のインスタンス**RecordsetEvent**クラスです。 これらの ADO/WFC クラス統合 ADO イベントのパラメーターです。つまり、各 ADO/WFC クラスにはすべて、ADO では一意のパラメーターごとに 1 つのデータ メンバーが含まれます**ConnectionEvent**または**RecordsetEvent**メソッドです。  
  
5.  ADO/WFC は、ADO/WFC イベント オブジェクトでイベント ハンドラーを呼び出します。 たとえば、 **onConnectComplete**ハンドラーには次のように署名します。  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    ```  
  
     最初の引数は、イベントを送信したオブジェクトの種類 ([接続](../../../ado/reference/ado-api/connection-object-ado.md)または[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md))、2 番目の引数は、ADO/WFC イベント オブジェクト (**ConnectionEvent**または**RecordsetEvent**)。  
  
     イベント ハンドラーのシグネチャは、ADO イベントよりも簡単です。 ただし、イベントに適用されるパラメーターと対処方法を知っている ADO イベント モデルを理解する必要があります。  
  
6.  イベント ハンドラーから、ADO/WFC イベントのハンドラーに、ADO を返します。 ADO/WFC ADO イベント パラメーターに適切な ADO/WFC イベントのデータ メンバーをコピーし、ADO のイベント ハンドラーを返します。  
  
7.  終了したら ADO/WFC イベント ハンドラーの一覧から、ハンドラーの削除を処理します。 など、名前のメソッドを使用して **removeOn** * EventName*(*ハンドラー*)。  
  
## <a name="see-also"></a>参照  
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO - WFC 構文のインデックス](../../../ado/reference/ado-api/ado-wfc-syntax-index.md)   
 [イベントのパラメーター](../../../ado/guide/data/event-parameters.md)   
 [イベント ハンドラーがどのように連携](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [イベントの種類](../../../ado/guide/data/types-of-events.md)
