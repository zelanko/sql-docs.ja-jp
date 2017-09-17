---
title: "ビジネス オブジェクトのスクリプトに対して安全としてマーク |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 0be98d1a-ab3d-4dce-a166-dacda10d154a
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 05a2131b594d20c4215a2c52422d930c0ac2edfb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="marking-business-objects-as-safe-for-scripting"></a>スクリプトを実行しても安全だとビジネス オブジェクトをマークします。
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 インターネット環境のセキュリティを確保するでインスタンス化される任意のビジネス オブジェクトをマークする必要があります、 [.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクトの[CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) "安全であるとします"メソッド。 ようにマークされているとライセンスの領域で、システム レジストリに DCOM を使用することを確認する必要があります。  
  
> [!NOTE]
>  「スクリプトを実行して安全な」または初期化に対して安全としてマークされているビジネス オブジェクトをインスタンス化され、ネットワーク経由ですべてのユーザーによって初期化されることができます。 ビジネス オブジェクトを「安全」にマークすることはありません、セーフであります。 これは、ビジネス オブジェクトがこのようなオブジェクトは、機微なデータの保護されていないアクセス ポイントを提示しないことを確認してください。 最上位のセキュリティとコード化されたかどうかを確認するきわめて重要です。  
  
 スクリプトを実行しても安全だとビジネス オブジェクトを手動でマークするには、次のテキストを含む .reg 拡張子を持つテキスト ファイルを作成します。 この例では\< *MyActiveXGUID*> ビジネス オブジェクトの 16 進数の GUID の数です。 次の 2 つの数値には、セーフ-スクリプトの機能が有効にします。  
  
```  
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}]  
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}]  
```  
  
 ファイルを保存し、レジストリ エディターを使用するか Windows エクスプ ローラーで、.reg ファイルをダブルクリックして、レジストリにマージします。  
  
 Microsoft Visual Basic で作成されたビジネス オブジェクトは、「スクリプトを実行しても安全だ」とで自動的にパッケージと展開ウィザードでマークできます。 ウィザードでは、安全性の設定を指定するよう求められます、ときに選択**初期化に対して安全**と**スクリプトに対して安全**です。  
  
 最後の手順では、アプリケーションのセットアップ ウィザードは、.htm ファイル、.cab ファイルを作成します。 ターゲット コンピューターにこれら 2 つのファイルをコピーし、ページを読み込むし、サーバーを正しく登録するには、.htm ファイルをダブルクリックします。  
  
 ビジネス オブジェクトは、既定で Windows\System32\Occache ディレクトリにインストールされるが、windows \system32 ディレクトリに移動し、変更、 **hkey_classes_root \clsid\\ ** \< *MyActiveXGUID*>\\**InprocServer32**レジストリ キーに正しいパスと一致します。



