# useQuery & Generic type

## useQuery type

- React Query를 사용하면서 query의 데이터에 대한 타입 지정이 필요
- 기본적으로는 any 타입을 받음
- useQuery는 제네릭 타입을 적극 지원
- useQuery<
  TQueryFnData = unknown,
  TError = unknown,
  TData = TQueryFnData,
  TQueryKey extends QueryKey = QueryKey

  >

  ```jsx
  const getStudentList = (): Promise<StudentInfomation[]> => {
      return axios
        .get<StudentInfomation[]>(`${STUDENT.LIST}`)
        .then((res) => res.data);
    };

    const { isSuccess, data } = useQuery<StudentInfomation[], AxiosError>(
      "studentList",
      getStudentList
    );
  ```

  - TQueryFnData
    query function의 return 값. 아래 코드에서는 getStudentList의 return 값인 [res.data](http://res.data) 의 타입. StudentInfomation[] | undefined의 타입을 가진다.
  - TError
    query function(getStudentList)의 error에 대한 타입.
    AxiosError | null의 값을 가진다.
  - TData
    query function의 “실질적인” return 값의 타입. TQueryFnData와 비슷하지만 다르다. useQuery는 select option을 통해 받아온 데이터를 2차 가공 후 return 할 수 있다. TData는 이 값에 대한 타입.
  - TQueryKey
    querykey(”studentList”)에 대한 타입.
    `export declare type QueryKey = string | readonly unknown[];`
    이렇게 타입을 받고있음. string이 아니라면 unknown[]이므로 직접 배열안에 타입을 지정해서 전달하면 된다.
