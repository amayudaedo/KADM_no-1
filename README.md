{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [],
   "source": [
    "import numpy as np\n",
    "import pandas as pd\n",
    "import matplotlib.pyplot as plt"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [],
   "source": [
    "data = pd.read_excel('C:/Intel/uas/dataset_soal No.1.xls')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Age</th>\n",
       "      <th>Income</th>\n",
       "      <th>Student</th>\n",
       "      <th>Credit_rating</th>\n",
       "      <th>Class (buy_computer)</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>&lt;= 30</td>\n",
       "      <td>High</td>\n",
       "      <td>No</td>\n",
       "      <td>Fair</td>\n",
       "      <td>No</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>&lt;= 30</td>\n",
       "      <td>High</td>\n",
       "      <td>No</td>\n",
       "      <td>Excellent</td>\n",
       "      <td>No</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>31..40</td>\n",
       "      <td>High</td>\n",
       "      <td>No</td>\n",
       "      <td>Fair</td>\n",
       "      <td>Yes</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>&gt; 40</td>\n",
       "      <td>Medium</td>\n",
       "      <td>No</td>\n",
       "      <td>Fair</td>\n",
       "      <td>Yes</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>&gt; 40</td>\n",
       "      <td>Low</td>\n",
       "      <td>Yes</td>\n",
       "      <td>Fair</td>\n",
       "      <td>Yes</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "      Age  Income Student Credit_rating Class (buy_computer)\n",
       "0   <= 30    High      No          Fair                   No\n",
       "1   <= 30    High      No     Excellent                   No\n",
       "2  31..40    High      No          Fair                  Yes\n",
       "3    > 40  Medium      No          Fair                  Yes\n",
       "4    > 40     Low     Yes          Fair                  Yes"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(51, 5)"
      ]
     },
     "execution_count": 18,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Low       21\n",
       "Medium    19\n",
       "High      11\n",
       "Name: Income, dtype: int64"
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data['Income'].value_counts()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [],
   "source": [
    "pYes = 40/50\n",
    "pNo = 10/50"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0.8\n"
     ]
    }
   ],
   "source": [
    "print(pYes)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0.2\n"
     ]
    }
   ],
   "source": [
    "print(pNo)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th>Income</th>\n",
       "      <th>High</th>\n",
       "      <th>Low</th>\n",
       "      <th>Medium</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Student</th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>No</th>\n",
       "      <td>9</td>\n",
       "      <td>1</td>\n",
       "      <td>14</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Yes</th>\n",
       "      <td>2</td>\n",
       "      <td>20</td>\n",
       "      <td>5</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "Income   High  Low  Medium\n",
       "Student                   \n",
       "No          9    1      14\n",
       "Yes         2   20       5"
      ]
     },
     "execution_count": 20,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "pd.crosstab(data['Student'], data['Income'])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
