- **Linie: 86** (`LinearLayout`) vs **100** (`ConstraintLayout`)
- **LinearLayout**:
  - W `LinearLayout` z ustawionym `android:orientation="vertical"` wystarczy wrzucać kolejne widoki jeden po drugim. Programiście odpada cała praca związana z pozycjonowaniem. System sam układa je w stosie z góry na dół, zgodnie z ich kolejnością występowania w pliku XML.
  - W czystym `ConstraintLayout`, aby ułożyć elementy jeden pod drugim na całym ekranie, dla każdego widoku musisz manualnie zdefiniować aż 3 atrybuty reguł, z czym on sąsiaduje (np. `app:layout_constraintTop_toBottomOf`, `app:layout_constraintStart_toStartOf`, `app:layout_constraintEnd_toEndOf`).
- Stanowczo łatwiej zaktualizować `LinearLayout`.
  - **LinearLayout**: Wystarczy „wkleić” nowy kod `<TextView>` oraz `<EditText>` w odpowiednie miejsce (np. między wiersze o haśle i e-mailu). Elementy znajdujące się poniżej zostaną samoczynnie „zepchnięte” na dół bez dotykania ich atrybutów.
  - **ConstraintLayout**: Wstawienie pola w środek zrywa tzw. łańcuch wiązań (Constraints). Jeśli wstawisz nowe pole pomiędzy *E-mail* a *Hasło*, to musisz:
    1. Ustalić nowe pole tak, aby podczepiało się do dołu *E-maila* (`constraintTop_toBottomOf="@id/editTextTextEmailAddress"`).
    1. Zaktualizować istniejące niżej pole *Hasło* tak, aby jego góra nie celowała już w *E-mail*, tylko właśnie spinała się z tym nowo dodanym widokiem.