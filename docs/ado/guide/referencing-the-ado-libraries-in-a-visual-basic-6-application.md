---
title: Visual Basic 6 アプリケーションで ADO ライブラリを参照する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual Basic application[ADO]
- ADO, libraries
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
author: rothja
ms.author: jroth
ms.openlocfilehash: 766707f8903f72da8b1735def4ed4433c4468d90
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747887"
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Visual Basic 6 アプリケーションで ADO ライブラリを参照する
Microsoft Visual Basic 6 アプリケーションに ADO ライブラリをインポートするには、Visual Basic プロジェクトで参照を設定する必要があります。  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>Visual Basic プロジェクト内の ADO ライブラリへの参照を設定するには  
  
1.  新しいを作成するか、既存の Visual Basic プロジェクトを開きます。  
  
2.  [**プロジェクト**] メニュー項目をクリックし、ドロップダウンメニューパネルから [**参照**] を選択します。  
  
3.  [**使用可能な参照**] で、[ **Microsoft ActiveX データオブジェクト*n. n*ライブラリ**] のチェックボックスをオンにします。 n は最新のバージョン番号***を表します***。 下の [**場所**] フィールドでは *$installDir \msado15.dll*として選択する必要があります。ここで *$installDir*は、ADO ライブラリがインストールされているディレクトリのパスを表します。  
  
4.  ADO MD を使用する場合は、手順 3. を繰り返して**Microsoft ActiveX データオブジェクト (多次元) *n. n*ライブラリ**を選択します。 [**場所**] フィールドでは、この選択を *$installDir*として指定する必要があります。  
  
5.  ADOX を使用する場合は、手順 3. を繰り返して、 **DDL およびセキュリティ用に MICROSOFT ADO Ext. *n. n* **を選択します。 [**場所**] フィールドでは、この選択を *$installDir \msadox.dll*として指定する必要があります。  
  
6.  [ **OK** ] をクリックして、参照の設定を完了します。  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 ADO をインストールすると、以前のバージョンの次のタイプライブラリもコピーされます。  
  
-   *msado27*、ADO 2.7 タイプライブラリ  
  
-   *msado26*、ADO 2.6 タイプライブラリ  
  
-   *msado25*、ADO 2.5 タイプライブラリ  
  
-   *msado21*、ADO 2.1 タイプライブラリ  
  
-   *msado20*、ADO 2.0 タイプライブラリ  
  
 旧バージョンとの互換性を保つために、アプリケーションでこれらの ADO ライブラリを使用する必要がある場合は、適切なバージョンのタイプライブラリをインポートする必要があります。 これを行うには、前のセクションの手順に従って、 *msadoXX*で*msado15.dll*を置き換えます。ここで、 *XX*はインポートする必要があるバージョン番号を表します。
