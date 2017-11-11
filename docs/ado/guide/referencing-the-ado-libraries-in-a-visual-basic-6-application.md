---
title: "Visual Basic 6 アプリケーションで ADO ライブラリを参照する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: "“drivers”"
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual Basic application[ADO]
- ADO, libraries
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a14a03b6b0a0e2e879d745fd8d2f341c1bbf6c54
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Visual Basic 6 アプリケーションで ADO ライブラリを参照します。
Microsoft Visual Basic 6 アプリケーションに、ADO ライブラリをインポートするには、Visual Basic プロジェクトで参照を設定する必要があります。  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>Visual Basic プロジェクトで、ADO ライブラリへの参照を設定するには  
  
1.  新規作成または既存の Visual Basic プロジェクトを開きます。  
  
2.  クリックして、**プロジェクト**クリックしてメニュー項目**参照しています.**ドロップ ダウン メニュー パネルからです。  
  
3.  **参照可能な**、チェック ボックスをオン**Microsoft ActiveX Data Objects *n.n*ライブラリ**ここで、 ***n.n***最新を表しますバージョン番号です。 **場所**下のフィールドとして選択を識別する必要があります*$installDir\msado15.dll*ここで、 *$installDir*するディレクトリのパスを表す、ADO ライブラリインストールされました。  
  
4.  ADO MD を使用する場合は、手順 3 を繰り返して選択**Microsoft ActiveX Data Objects (多次元) *n.n*ライブラリ**です。 **場所**フィールドとしてこの選択を識別する必要があります*$installDir\msadomd.dll*です。  
  
5.  ADOX を使用する場合は、手順 3 を繰り返して選択**Microsoft ADO 内線*n.n* DDL およびセキュリティ用**です。 **場所**フィールドとしてこの選択を識別する必要があります*$installDir\msadox.dll*です。  
  
6.  をクリックして**OK**参照の設定を完了します。  
  
## <a name="backward-compatibility"></a>旧バージョンとの互換性  
 ADO をインストールすると、以前のバージョンの次のタイプ ライブラリもコピーします。  
  
-   *msado27.tlb*、ADO 2.7 タイプ ライブラリ  
  
-   *msado26.tlb*、ADO 2.6 のタイプ ライブラリ  
  
-   *msado25.tlb*、ADO 2.5 のタイプ ライブラリ  
  
-   *msado21.tlb*、ADO 2.1 のタイプ ライブラリ  
  
-   *msado20.tlb*、ADO 2.0 タイプ ライブラリ  
  
 アプリケーションではこれらの ADO ライブラリを使用の旧バージョンと互換性の理由から必要がある場合は、タイプ ライブラリの適切なバージョンをインポートする必要があります。 これを行うには、前のセクションの手順に従います交換*msado15.dll*によって*msadoXX.tlb*ここで、 *XX*をインポートする必要があります。 バージョン番号を表します。

