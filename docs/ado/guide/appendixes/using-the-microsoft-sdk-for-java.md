---
title: Microsoft SDK を使用した Java |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Java (Microsoft SDK for)
- Microsoft SDK for Java [ADO]
ms.assetid: 2d7cb5b5-8307-49dd-b07e-c07069bb1626
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b12135a32e66e18a32961abe95dc35bb333e2f4
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="using-the-microsoft-sdk-for-java"></a>Java の Microsoft SDK を使用します。

> [!IMPORTANT]
> Microsoft では、2004 年 1 月で Visual j のサポートが廃止されました。

Microsoft SDK for Java は、Microsoft Internet Explorer の環境の開発キットです。 ツール、情報、およびサンプルは、Java プログラムと JDK 1.1 および Microsoft Win32 仮想マシン (Microsoft VM) に基づくアプレットを開発するために提供されます。 Microsoft SDK for Java が関連付けられていないに Microsoft Visual j です。 この SDK をダウンロードするには、ここをクリックします。  
  
 Jactivex.exe ユーティリティでは、タイプ ライブラリからクラスが生成されますが、コマンドラインでのみ呼び出すことができます。 この機能は、Visual j 開発環境と統合されていません。 クラスと異なり、Java タイプ ライブラリ ウィザードによって生成された、ステップ インできます SDK によって作成されたクラスのラッパー。 これは、コードが ADO ラッパー クラスを使用する方法のデバッグに役立ちます。  
  
 このメカニズムは、ADO タイプ ライブラリを読み込んで、アプリケーション内でインスタンス化できるクラスを生成します。 次の場所にこれらのクラスが生成されます: \\< windows ディレクトリ\>\Java\trustlib\msado15 です。  
  
 For Java の Microsoft SDK を使用して Java で ADO アプリケーションの作成は、基本的に同じですが、ソース コードの観点から Java タイプ ライブラリのウィザードを使用してです。 サンプル コードは、次を参照してください。 [Java クラス ラッパーを ADO](../../../ado/guide/appendixes/ado-java-class-wrappers.md)です。 唯一の違いは、まず、次の手順で示したように、ラッパー クラスを生成する方法です。  
  
### <a name="to-create-an-ado-project-with-the-microsoft-sdk-for-java"></a>Microsoft SDK for Java で ADO プロジェクトを作成するには  
  
1.  コマンド プロンプトで、次を実行します。 Microsoft SDK for Java の Bin ディレクトリを格納するパスを設定またはその場所からのコマンドを実行する必要があります。 通常、Microsoft SDK for Java は Visual Studio と同じ場所にインストールします。 これは、1 つのコマンド ステートメントです。  
  
    ```  
    \<path to DevStudio>\<path to Java SDK>\bin\JactiveX.exe /javatlb "C:\program files\common files\system\ado\msado15.dll"  
    ```  
  
2.  生成されたクラスをコンパイルするには、次のコマンドを実行します。 トレースすることができるように、デバッグ シンボルの生成を/g:t スイッチがオンにします。Java 記号。 リリース ビルドを削除します。  
  
    ```  
    jvc /g:t c:\<windows>\Java\trustlib\msado15\*.Java  
    ```  
  
3.  これらのファイルを使用するには、プロジェクトを開く、Visual j です。 **プロジェクト**] メニューの [選択**プロジェクトに追加**です。 選択**ファイル**、すべての追加とします。JAVA ファイルがプロジェクトに trustlib\msado15 ディレクトリに生成します。  
  
## <a name="see-also"></a>参照  
 [ADO Java クラス ラッパー](../../../ado/guide/appendixes/ado-java-class-wrappers.md)   
