---
title: 手順 1:Node.js 用に開発環境を構成する
description: SQL Server 用の Node.js ドライバーを使用してアプリケーションを開発するには、前提条件を使用して開発環境を構成する必要があります。
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 38337772d9ec9db2503637122d0d1b616dc6ef5f
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528136"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>手順 1:Node.js 開発用に開発環境を構成する
SQL Server 用の Node.js ドライバーを使用してアプリケーションを開発するには、前提条件を使用して開発環境を構成する必要があります。  最も一般的な方法は、ノード パッケージ マネージャー (npm) を使用して面倒なモジュールをインストールすることですが、必要に応じて [GitHub](https://github.com/pekim/tedious) で面倒なモジュールを直接ダウンロードすることもできます。  
  
Node.js ドライバーでは TDS プロトコルが使用されます。これは SQL Server と Azure SQL Database で既定で有効になっています。  追加の構成は不要です。  
  
## <a name="windows"></a>Windows  
  
1. **Node.js ランタイムと npm パッケージ マネージャーをインストールします。**  
a. [Node.js](https://nodejs.org/en/download/) にアクセスします  
b. 適切な Windows インストーラーの msi リンクをクリックします。   
c. ダウンロードが完了したら、msi を実行して Node.js をインストールします  
  
2. **cmd.exe を開きます**  
  
3. **プロジェクト ディレクトリを作成**し、それに移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **ノード プロジェクトを作成します。**  プロジェクトの作成時に既定値を保持するには、プロジェクトが作成されるまで Enter キーを押します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルが表示されます。  
```  
> npm init  
```  
  
5. **tedious モジュールをプロジェクトにインストールします。**  tedious は、SQL Server への通信に使用される TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **ターミナルを開きます**  
  
2. **Node.js ランタイムをインストールします。**  
```  
>sudo apt-get install node  
```  
3. **npm (ノード パッケージ マネージャー) をインストールします。**  
```  
> sudo apt-get install npm  
```  
4. **プロジェクト ディレクトリを作成**し、それに移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **ノード プロジェクトを作成します。**  プロジェクトの作成時に既定値を保持するには、プロジェクトが作成されるまで Enter キーを押します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルが表示されます。  
```  
> sudo npm init  
```  
  
6. **tedious モジュールをプロジェクトにインストールします。**  tedious は、SQL Server への通信に使用される TDS プロトコルの実装です。  
```  
> sudo npm install tedious  
```  
  
## <a name="macos"></a>macOS  
  
1. **Node.js ランタイムと npm パッケージ マネージャーをインストールします。**  
a. [Node.js](https://nodejs.org/en/download/) にアクセスします  
b. 適切な macOS インストーラーのリンクをクリックします。  
c. ダウンロードが完了したら、"dmg" を実行して Node.js をインストールします  
  
2. **ターミナルを開きます**  
  
3. **プロジェクト ディレクトリを作成**し、それに移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **ノード プロジェクトを作成します。**  プロジェクトの作成時に既定値を保持するには、プロジェクトが作成されるまで Enter キーを押します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルが表示されます。  
```  
> npm init  
```  
  
5. **tedious モジュールをプロジェクトにインストールします。**  これは、ドライバーが SQL Server と通信するために使用する TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
