---
title: 'ステップ 1: Node.js 開発用に開発環境を構成する | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 49522e397789c5193ed8f218a5fdf776ba62f001
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799362"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>ステップ 1: Node.js 開発用に開発環境を構成する
SQL Server 用 Node.js ドライバーを使用してアプリケーションを開発するために、前提条件、開発環境を構成する必要があります。  ノード パッケージ マネージャー (npm) を使用して、面倒なモジュールをインストールする最も一般的な方法がダウンロードできるは面倒なモジュールに直接[Github](https://github.com/pekim/tedious)したい場合。  
  
Node.js ドライバーが SQL Server と Azure SQL Database での既定で有効になっている TDS プロトコルを使用することに注意してください。  追加の構成は必要ありません。  
  
## <a name="windows"></a>Windows  
  
1. **Node.js ランタイムと npm パッケージ マネージャーをインストールします。**  
A. 移動して[Node.js](https://nodejs.org/en/download/)  
B. 適切な Windows インストーラーの msi リンクをクリックします。   
c. Node.js をインストールする msi をダウンロードしたら、実行します。  
  
2. **Cmd.exe を開きます**  
  
3. **プロジェクト ディレクトリを作成**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **ノードのプロジェクトを作成します。**  プロジェクトの作成中に、既定値を保持するには、キーを押して、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルを参照してください必要があります。  
```  
> npm init  
```  
  
5. **プロジェクトで面倒なモジュールをインストールします。**  これは、ドライバーが SQL Server との通信に使用する、TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **ターミナルを開く**  
  
2. **Node.js ランタイムをインストールします。**  
```  
>sudo apt-get install node  
```  
3. **Npm (ノード パッケージ マネージャー) をインストールします。**  
```  
> sudo apt-get install npm  
```  
4. **プロジェクト ディレクトリを作成**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **ノードのプロジェクトを作成します。**  プロジェクトの作成中に、既定値を保持するには、キーを押して、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルを参照してください必要があります。  
```  
> sudo npm init  
```  
  
6. **プロジェクトで面倒なモジュールをインストールします。**  これは、ドライバーが SQL Server との通信に使用する、TDS プロトコルの実装です。  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Node.js ランタイムと npm パッケージ マネージャーをインストールします。**  
A. 移動して[Node.js](https://nodejs.org/en/download/)  
B. 該当する Mac OS インストーラー リンクをクリックします。  
c. Node.js をインストールする dmg をダウンロードしたら、実行します。  
  
2. **ターミナルを開く**  
  
3. **プロジェクト ディレクトリを作成**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **ノードのプロジェクトを作成します。**  プロジェクトの作成中に、既定値を保持するには、キーを押して、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルを参照してください必要があります。  
```  
> npm init  
```  
  
5. **プロジェクトで面倒なモジュールをインストールします。**  これは、ドライバーが SQL Server との通信に使用する、TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  
