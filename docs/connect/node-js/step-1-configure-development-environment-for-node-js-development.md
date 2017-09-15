---
title: "手順 1: Node.js 開発のための開発環境の構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b4e41033ffb30801fd388f7816c34c8a7751daa9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>手順 1: Node.js 開発のための開発環境を構成します。
SQL Server の Node.js のドライバーを使用してアプリケーションを開発するために、前提条件と開発環境を構成する必要があります。  面倒のモジュールをインストールするノードのパッケージ マネージャー (npm) を使用する最も一般的な方法ですが、直接に面倒なモジュールをダウンロードする[Github](https://github.com/pekim/tedious)したい場合。  
  
Node.js ドライバーが SQL Server と Azure SQL データベースで既定で有効になっている TDS プロトコルを使用することに注意してください。  追加の構成は必要ありません。  
  
## <a name="windows"></a>Windows  
  
1. **Node.js のランタイムと npm パッケージ マネージャーをインストールします。**  
a. 移動して[Node.js](https://nodejs.org/en/download/)  
b. Windows インストーラー msi の適切なリンクをクリックします。   
c. ダウンロードされると、Node.js をインストールする msi を実行します。  
  
2. **Cmd.exe を開きます**  
  
3. **プロジェクト ディレクトリを作成する**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **ノードのプロジェクトを作成します。**  プロジェクトの作成時に、既定値を保持するには、キーを押しては、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリ package.json ファイルが表示されます。  
```  
> npm init  
```  
  
5. **プロジェクトに面倒なモジュールをインストールします。**  これは、ドライバーは SQL Server との通信を使用して、TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **開いているターミナル**  
  
2. **Node.js のランタイムをインストールします。**  
```  
>sudo apt-get install node  
```  
3. **Npm (パッケージ マネージャーのノード) のインストールします。**  
```  
> sudo apt-get install npm  
```  
4. **プロジェクト ディレクトリを作成する**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **ノードのプロジェクトを作成します。**  プロジェクトの作成時に、既定値を保持するには、キーを押しては、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリ package.json ファイルが表示されます。  
```  
> sudo npm init  
```  
  
6. **プロジェクトに面倒なモジュールをインストールします。**  これは、ドライバーは SQL Server との通信を使用して、TDS プロトコルの実装です。  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Node.js のランタイムと npm パッケージ マネージャーをインストールします。**  
a. 移動して[Node.js](https://nodejs.org/en/download/)  
b. Mac OS インストーラーの適切なリンクをクリックします。  
c. ダウンロードされると、実行、dmg Node.js をインストールするには  
  
2. **開いているターミナル**  
  
3. **プロジェクト ディレクトリを作成する**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **ノードのプロジェクトを作成します。**  プロジェクトの作成時に、既定値を保持するには、キーを押しては、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリ package.json ファイルが表示されます。  
```  
> npm init  
```  
  
5. **プロジェクトに面倒なモジュールをインストールします。**  これは、ドライバーは SQL Server との通信を使用して、TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  

