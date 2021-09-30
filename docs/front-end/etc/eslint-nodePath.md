# eslint.nodePath

- vscode에서 eslint-plugin은 global mode 설정이 정상적으로 반영이 안돼, 전역사용이 안된다.
- 최상위 폴더에 eslint 및 eslint-plugin 설치 후, eslint를 사용해야하는 하위 디렉토리마다 `eslint.nodePath` 설정을 통해 직접 `node_modules` 설정을 해줘야 한다.
  [feat: Remove relative dependencies on demo/with-cra by milooy · Pull Request #214 · EveryAnalytics/react-analytics-provider · GitHub](https://github.com/EveryAnalytics/react-analytics-provider/pull/214#issue-1007357343)
